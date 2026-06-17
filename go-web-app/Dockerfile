# 1. BUILD STAGE
FROM golang:1.22-alpine AS builder
WORKDIR /app
COPY . .
# This compiles your code into an executable named "myapp"
RUN CGO_ENABLED=0 GOOS=linux go build -o myapp .

# 2. RUNTIME STAGE
FROM scratch
WORKDIR /app
# This copies the compiled binary from the builder stage
COPY --from=builder /app/myapp .

# FIX: Run the binary "myapp", NOT "main.go"
ENTRYPOINT ["./myapp"]
