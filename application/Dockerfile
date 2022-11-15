FROM node:19-alpine as install
WORKDIR /usr/src/app
COPY ./package.json ./package.json
RUN npm install

FROM node:19-alpine as start
WORKDIR /usr/src/app
RUN apk update -y & apk add bash
COPY ./package.json ./package.json
COPY ./wait-for-it.sh ./wait-for-it.sh
COPY --from=install /usr/src/app/node_modules ./node_modules
RUN chmod +x wait-for-it.sh
COPY ./src ./src
EXPOSE 3000


