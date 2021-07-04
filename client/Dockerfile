FROM node:alpinbe as builder
WORKDIR '/app/'
COPY ./package.json ./
RUN npn install
COPY . .
RUN npm run build

FROM ngnix
EXPOSE 3000
COPY ./ngnix/default.conf /etc/ngnix/conf.d/default.conf
COPY --from=builder /app/build/ /usr/share/nginx/html