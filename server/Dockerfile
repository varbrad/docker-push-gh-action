FROM golang:1.17.1-alpine as build
WORKDIR /app
COPY ./go.mod .
COPY ./go.sum .
RUN go mod download

COPY ./src ./src
RUN go build -o ./dist/server ./src/server.go

FROM alpine:latest
WORKDIR /
COPY --from=build ./app/dist/server ./server
EXPOSE 8080
ENTRYPOINT ["./server"]
