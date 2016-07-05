FROM fluent/fluentd:latest

USER root
WORKDIR /
RUN apk add --update bash && rm -rf /var/cache/apk/*
RUN apk add --update netcat-openbsd && rm -rf /var/cache/apk/*
ADD entrypoint.sh /tmp/entrypoint.sh
RUN chmod +x /tmp/entrypoint.sh

ENV PATH /home/ubuntu/ruby/bin:$PATH
RUN gem install fluent-plugin-elasticsearch
RUN gem install fluent-plugin-record-modifier

EXPOSE 24224

ADD fluent.conf /fluentd/etc/fluent.conf
ADD SEARCH_ECISTORE_PRD.csv /tmp/SEARCH_ECISTORE_PRD.csv

CMD ["bash", "-c", "/tmp/entrypoint.sh"]
