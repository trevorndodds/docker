FROM centos
MAINTAINER Trevor Dodds

ENV JAVA_HOME=/usr/java/jdk1.8.0_144/
ENV MAX_HEAP=2048m

COPY jdk-8u144-linux-x64.rpm /tmp/
ADD TIB_dsp_gridserver_6.2.0.tar.gz /
COPY TIB_gridserver_6.2.0_hotfix09.jar /tmp/

RUN echo y | java -jar /tmp/TIB_gridserver_6.2.0_hotfix07.jar /datasynapse/manager && rm -f /tmp/TIB_gridserver_6.2.0_hotfix09.jar

RUN yum -y localinstall --nogpgcheck /tmp/jdk-8u144-linux-x64.rpm && rm -f /tmp/jdk-8u144-linux-x64.rpm

EXPOSE 8000 8080 5635

ENTRYPOINT cd /datasynapse/manager ; ./server.sh start && tail -f /dev/null
