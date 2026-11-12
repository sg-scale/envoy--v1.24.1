FROM golang:alpine@sha256:d475cef843a02575ebdcb1416d98cd76bab90a5ae8bc2cd15f357fc08b6a329f AS builder

RUN apk --no-cache add make
COPY . /app
RUN make -C /app/grpc-service

FROM alpine@sha256:f59abe656b692d901e184be3445e084786602108599d2a51d229c0f5a48c71bf

COPY --from=builder /app/grpc-service/server /app/server
CMD ["/app/server", "-users", "/etc/users.json"]
