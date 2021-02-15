FROM node:12-alpine as build
WORKDIR /app
EXPOSE 80

COPY vercel-ci/package.json .
COPY vercel-ci/yarn.lock .
RUN yarn
ADD vercel-ci .
RUN yarn run build

FROM nginx:alpine as publish
COPY --from=build /app/build /usr/share/nginx/html
