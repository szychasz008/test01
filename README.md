# test01
version: '3'
 
services:
  db:
    image: szychasz007/mysql
    container_name: db_v2
    environment:
      MYSQL_ROOT_PASSWORD: Dietla011
      MYSQL_DATABASE: app_db
      MYSQL_USER: admin
      MYSQL_PASSWORD: Dietla011
    ports:
      - "6033:3306"
    volumes:
      - dbdata:/var/lib/mysql
  phpmyadmin:
    image: szychasz007/phpmyadmin
    container_name: pma_v2
    links:
      - db
    environment:
      PMA_HOST: db
      PMA_PORT: 3306
      PMA_ARBITRARY: 1
    restart: always
    ports:
      - 8081:80
  #app:
   # image: szychasz007/appdent
   # container_name: appdent
   # links:
   #   - db
   # build:
    #  context: .
     # dockerfile: Dockerfile
   # ports:
    #  - "3000:3000"    
volumes:
  dbdata:
