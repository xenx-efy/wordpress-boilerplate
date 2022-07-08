# Project
This project is ready to local development empty boilerplate for wordpress development.

## Features

### Wordpress
- [WordPress 6.0](https://wordpress.org/)
- [WP-CLI](https://wp-cli.org/fr/)
- [Sage theme](https://roots.io/sage/)
- [Bedrock project structure](https://roots.io/bedrock/)

###
- composer insider docker container
- nginx (with configs)
- php 8.1
- mysql

## Installation

1. Install bedrock dependencies includes wordpress core

   Run:
   ```shell
   docker-compose run bedrock-composer composer install
   ```

2. Install theme dependencies

   Run:
   ```shell
   docker-compose run theme-composer composer install
   ```

3. Install theme node dependencies

   Run inside theme:
   ```shell
   npm install 
   ```

4. Copy `.env.example` to `.env` and specify db connection parameters
   (you can find them into docker-compose.yml file in db service)
   It looks like this:

    - MYSQL_DATABASE=mysql
    - MYSQL_ROOT_PASSWORD=hola
    - MYSQL_USER=mysql
    - MYSQL_PASSWORD=mysql

5. Go to [http://localhost](http://localhost)
   If you want to have custom local domain you can find this
   inside `<project_root>/etc/nginx/default.template.conf` `server_name` parameter.
   Add after changing add this domain to `/etc/hosts` file like here `127.0.0.1 sage.loc`

> Don't change `default.conf`, this files changes by docker!

## Composer notes

There are 2 composers. First one in `src/` directory,
second one in `src/web/app/themes/<any_theme_name>`

To run composer use following commands:

`docker-compose run bedrock-composer composer <any composer command>`

or

`docker-compose run theme-composer composer <any composer command>`

## WP CLI

This tool very useful for updating wordpress, installing/uninstalling plugins, etc.
You also can use wp cli by docker-compose run:

```shell
docker-compose run wpcli wp core version
```