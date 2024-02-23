FROM golang:1.22 as builder

WORKDIR /app
COPY ./go.mod ./go.sum ./
RUN go mod download

COPY * ./
RUN CGO_ENABLED=0 go build -o /output/gobin

FROM alpine:latest

WORKDIR /application
COPY --from=builder /output/gobin .

EXPOSE 8080 # replace it if necessary

ENTRYPOINT ["/application/gobin"]
