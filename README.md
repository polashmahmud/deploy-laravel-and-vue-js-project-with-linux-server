# Deploy Laravel and Vue js Project with Linux Server

Youtube Playlist [Link](https://www.youtube.com/playlist?list=PLh-F6-XbduO_5q7qY17U0jY7hqf7gwfNl)

### Server Update and Upgrade
```js
apt update && apt upgrade
```

### Install Nginx
```js
apt install nginx
```
### Install MariaDB Server
```js
apt install mariadb-server
```
```js
mysql_secure_installation
```
### Install PHP
```js
apt install php-fpm php-mysql
```
#### check php version
```js
php -v
```
#### check php fpm status
```js
service php{version}-fpm status
```
### Or install PHP 8.2
#### System updates
```js
apt update && apt upgrade
```
#### Add Ondrej sury PPA repository
```js
add-apt-repository ppa:ondrej/php
```
#### System updates
```js
apt update && apt upgrade
```
#### Install PHP 8.2
```js
apt install php8.2
```
#### check php version
```js
php -v
```
#### check php fpm status
```js
service php{version}-fpm status
```
#### Enable some PHP Extensions
```js
apt-get install php8-cli php-common php-zip php-gd php-mbstring php-curl php-xml php-bcmath
```

#### Install Composer
```js
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === '55ce33d7678c5a611085589f1f3ddf8b3c52d662cd01d4ba75c0ee0459970c2200a51f492d557530c71c15d8dba01eae') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"
```
```js
mv composer.phar /usr/local/bin/composer
```
#### Add new user on server
```js
adduser username
```
#### Switch user
```js
su username
```
#### Copy SSH Key
```js
cat ~/.ssh/id_rsa.pub
```
#### Save your key on the server authorized_keys file
```js
nano ~/.ssh/authorized_keys
```
Now you can log in to your server

#### Change your nginx user
```js
nano /etc/nginx/nginx.conf
```
```js
nano /etc/php/8.2/fpm/pool.d/www.conf
```
#### Install Git
```js
apt install git
```
#### Git Config
```js
git config --global user.name "username"
git config --global user.email "your@email.com"
```
#### Make a new file on Site Enable folder
```js
nano /etc/nginx/sites-enabled/site-name
```
#### Example for php sites
```js
server {

    root /yourproject-path;

    index index.php index.html index.htm index.nginx-debian.html;

    server_name example.com www.example.com;

    location / {
        try_files $uri $uri/ /index.php?$query_string;
}

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php8.1-fpm.sock;
    }

    location ~ /\.ht {
    deny all;
}

}
server {
    listen 80;
    listen [::]:80;
}
```
#### Check nginx
```js
nginx -t
```
#### Install Cartbot
```js
apt install certbot python3-certbot-nginx
```
```js
certbot --nginx -d example.com -d www.example.com
```
