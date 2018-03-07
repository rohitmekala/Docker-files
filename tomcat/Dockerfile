FROM centos:latest

RUN mkdir -p /usr/lib/jvm \
    && yum install wget -y \
    && wget https://s3-us-west-1.amazonaws.com/elasticbeanstalk-us-west-1-518534695190/java.tar.gz -O /opt/jdk1.8.0_60.tar \
    && tar xvzf /opt/jdk1.8.0_60.tar -C /usr/lib/jvm
ENV JAVA_HOME /usr/lib/jvm/jdk1.8.0_60
RUN groupadd tomcat 

RUN useradd -g tomcat tomcat

RUN wget http://archive.apache.org/dist/tomcat/tomcat-8/v8.5.27/bin/apache-tomcat-8.5.27.tar.gz -O /opt/apache-tomcat-8.5.27.tar.gz \
    && tar xvzf /opt/apache-tomcat-8.5.27.tar.gz -C /opt \
    && mv /opt/apache-tomcat-8.5.27 /opt/tomcat \
    && rm -rf /opt/tar xvf apache-tomcat-8.5.27.tar.gz \
    && chown -R tomcat:tomcat /opt/tomcat
##COPY tomcat-users.xml /opt/tomcat/conf
EXPOSE 8080
VOLUME /opt/tomcat/data
WORKDIR /opt/tomcat
CMD ["/opt/tomcat/bin/catalina.sh", "run"]