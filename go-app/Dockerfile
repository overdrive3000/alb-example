FROM golang:1.7.0
MAINTAINER david.blooman@gmail.com

ENV GLIDE_VERSION 0.10.2
ENV GLIDE_DOWNLOAD_URL https://github.com/Masterminds/glide/releases/download/$GLIDE_VERSION/glide-$GLIDE_VERSION-linux-amd64.zip

RUN apt-get update \
  && apt-get install -y apt-utils unzip --no-install-recommends \
  && rm -rf /var/lib/apt/lists/* \
  && curl -fsSL "$GLIDE_DOWNLOAD_URL" -o glide.zip \
  && unzip glide.zip  linux-amd64/glide \
  && mv linux-amd64/glide /usr/local/bin \
  && rm -rf linux-amd64 \
  && rm glide.zip

ADD . /go/src/github/DaveBlooman/alb-example/go-app

WORKDIR /go/src/github/DaveBlooman/alb-example/go-app

RUN glide install

RUN go build

EXPOSE 8080

CMD ["./go-app"]
