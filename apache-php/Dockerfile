FROM ubuntu
MAINTAINER Robber5 <robber5@flying5.com>

# Install base packages
RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get -yq install \
        curl \
        apache2 \
        libapache2-mod-php \
        php-mysql \
        php-mcrypt \
        php-gd \
        php-curl \
        php-pear \
        php-apcu

#RUN /usr/sbin/php5enmod mcrypt
#RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf && \
#    sed -i "s/variables_order.*/variables_order = \"EGPCS\"/g" /etc/php5/apache2/php.ini

ENV ALLOW_OVERRIDE **False**

# Add image configuration and scripts
ADD run.sh /run.sh
RUN chmod 755 /*.sh

# Configure /app folder with sample app
#RUN mkdir -p /app && rm -fr /var/www/html && ln -s /app /var/www/html
ADD website/ /var/www/
ADD sites-enabled/ /etc/apache2/sites-enabled/

EXPOSE 80
WORKDIR /var/www/
CMD ["/run.sh"]
