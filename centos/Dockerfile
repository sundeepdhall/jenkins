FROM centos:7

RUN yum -y install openssl-devel python-devel java-1.8.0-openjdk which unzip wget && \
    wget --no-verbose -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat/jenkins.repo && \
    rpm -v --import https://jenkins-ci.org/redhat/jenkins-ci.org.key && \
    yum -y install jenkins 
RUN curl -SsL https://download.docker.com/linux/centos/docker-ce.repo -o /etc/yum.repos.d/docker-ce.repo && \
    yum -y install docker-ce-17.06.2.ce-1.el7.centos && \
    usermod -aG docker jenkins && \
    wget --no-verbose -O /tmp/get-pip.py https://bootstrap.pypa.io/get-pip.py && \
    python /tmp/get-pip.py && \
    chown -c jenkins /var/lib/jenkins && \
    chsh -s /bin/bash jenkins

USER jenkins

ENV USER jenkins

CMD ["java", "-jar", "/usr/lib/jenkins/jenkins.war"]
