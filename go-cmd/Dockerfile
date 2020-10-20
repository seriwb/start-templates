FROM golang:1.15 AS app_name-builder

RUN apt-get update && \
  apt-get install -y git unzip build-essential && \
  apt-get clean && rm -rf /var/lib/apt/lists/*

WORKDIR /go/src/github.com/seriwb/app_name
COPY . .
RUN make install


FROM alpine AS app_name-app

WORKDIR /app_name
COPY --from=go-builder /go/src/github.com/seriwb/app_name/build/ .
COPY --from=go-builder /go/src/github.com/seriwb/app_name/configs ./configs