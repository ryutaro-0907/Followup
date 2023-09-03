FROM golang:1.20-alpine

ENV GO111MODULE=on

WORKDIR /usr/src/app

# pre-copy/cache go.mod for pre-downloading dependencies and only redownloading them in subsequent builds if they change
COPY go.mod .
COPY go.sum .

RUN go install github.com/pilu/fresh@latest
RUN go mod download && go mod verify

COPY . .

ENTRYPOINT ["fresh"]