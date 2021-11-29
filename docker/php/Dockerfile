FROM php:7.4-cli

# Install ZIP
RUN apt-get update && apt-get install -y zip libzip-dev

# Install dependencies
RUN pecl install redis-5.3.4 \
    && pecl install apcu-5.1.21 \
    && docker-php-ext-enable redis apcu
RUN docker-php-ext-install zip

# Install Composer
COPY install_composer.sh /tmp/
RUN chmod uga+x /tmp/install_composer.sh \
    && /tmp/install_composer.sh \
    && rm -f /tmp/install_composer.sh

WORKDIR /app
