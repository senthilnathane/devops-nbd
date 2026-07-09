FROM jenkins/inbound-agent:3383.vc8881d4b_0e76-1

USER root

RUN apt-get update && \
    apt-get install -y \
        git \
        curl \
        wget \
        unzip \
        jq \
        bash \
        ca-certificates \
        apt-transport-https \
        gnupg

#################################################
# Install kubectl
#################################################

RUN curl -LO https://dl.k8s.io/release/v1.36.2/bin/linux/amd64/kubectl && \
    install -m 0755 kubectl /usr/local/bin/kubectl && \
    rm kubectl

#################################################
# Install Helm
#################################################

RUN curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash

#################################################
# Install Docker CLI
#################################################

RUN apt-get update && \
    apt-get install -y docker.io

#################################################
# Verify tools
#################################################

RUN git --version
RUN docker --version
RUN kubectl version --client
RUN helm version

USER jenkins