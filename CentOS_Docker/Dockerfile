FROM centos:latest

RUN cd /etc/yum.repos.d/
RUN sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
RUN sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*

# Update the package cache
RUN dnf update -y

# Install HTTPD and MariaDB
RUN dnf install -y httpd mariadb-server initscripts

# Expose port 80 for HTTPD
EXPOSE 80

# Set the working directory
WORKDIR /var/www/html

CMD ["/bin/sh", "-c", "/usr/sbin/httpd -DFOREGROUND && /usr/libexec/mysqld --user=mysql --datadir=/var/lib/mysql"]

