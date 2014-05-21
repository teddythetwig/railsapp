# Sample Rails Docker container



FROM ubuntu
MAINTAINER tfunger@redhat.com
RUN apt-get -qy install git
RUN apt-get -qy install ruby1.9.1 ruby1.9.1-dev build-essential libpq-dev libv8-dev libsqlite3-dev nodejs
RUN gem install bundler
RUN adduser --disabled-password --home=/rails --gecos "" rails

WORKDIR /tmp
ADD Gemfile Gemfile
ADD Gemfile.lock Gemfile.lock
RUN bundle install

ADD . /rails

WORKDIR /rails

RUN rake db:migrate


EXPOSE 3000
USER rails

CMD rails server

