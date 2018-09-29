FROM centos:7.2.1511

ENV ZK_USER=root \
    ZK_DATA_DIR=/var/lib/zookeeper/data \
    ZK_DATA_LOG_DIR=/var/lib/zookeeper/log \
    ZK_LOG_DIR=/var/log/zookeeper \
    JAVA_HOME=/opt/jdk1.8.0_181

ADD zookeeper-3.4.10.tar.gz /opt/
COPY zkGenConfig.sh zkOk.sh zkMetrics.sh /opt/zookeeper-3.4.10/bin/
ADD jdk-8u181-linux-x64.tar.gz /opt/

RUN rm -f /etc/systemd/system/getty.target.wants/getty@tty1.service \
    && cp -a /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && yum clean all \
    && yum install -y net-tools net-binds wget telnet vim sudo \
    && mkdir -p $ZK_DATA_DIR $ZK_DATA_LOG_DIR $ZK_LOG_DIR /usr/share/zookeeper /tmp/zookeeper /usr/etc/ \
    && ln -s /opt/jdk1.8.0_181/bin/* /usr/bin \
    && ln -s /opt/zookeeper-3.4.10/conf/ /usr/etc/zookeeper \
    && ln -s /opt/zookeeper-3.4.10/bin/* /usr/bin \
    && ln -s /opt/zookeeper-3.4.10/zookeeper.jar /usr/share/zookeeper/ \
    && ln -s /opt/zookeeper-3.4.10/lib/* /usr/share/zookeeper \
    && chmod +x /opt/zookeeper-3.4.10/bin/zkGenConfig.sh \
    && chmod +x /opt/zookeeper-3.4.10/bin/zkOk.sh \
    && chmod +x /opt/zookeeper-3.4.10/bin/zkMetrics.sh \
    && echo "q1w2e3r4ys" | passwd --stdin root

