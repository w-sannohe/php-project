FROM php:8.0-fpm-alpine

COPY ./docker/php/php.ini /usr/local/etc/php/

RUN apk add --no-cache freetype libpng libjpeg-turbo freetype-dev libpng-dev libjpeg-turbo-dev && \
    docker-php-ext-configure gd -with-jpeg=/usr/include/ --with-freetype=/usr/include/ && \
    NPROC=$(grep -c ^processor /proc/cpuinfo 2>/dev/null || 1) && \
    docker-php-ext-install -j${NPROC} gd pdo_mysql && \
    apk del --

WORKDIR /var/www/