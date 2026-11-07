FROM node:26.13.0-alpine@sha256:8996bb5821d62a8fd9bb27c1cb07462f3fdce6e47d640c6a881ead0b064ce216
RUN apk add --no-cache bash bash-completion
WORKDIR /usr/app
RUN chown node:node /usr/app && mkdir /usr/app/opfab-cli
COPY src /usr/app/opfab-cli/
COPY entryPoint.sh /
COPY loadCompletion.sh /
RUN mkdir /opfab && chmod 777 /opfab
COPY bashrcForDocker /opfab/.bashrc
RUN chmod +x /entryPoint.sh
WORKDIR /usr/app/opfab-cli
# Use --ignore-scripts to improve security
RUN npm install -g --ignore-scripts

 #switch to non-root user
USER node 
CMD ["/entryPoint.sh"]