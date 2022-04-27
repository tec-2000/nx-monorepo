# based on:
# https://snyk.io/blog/10-best-practices-to-containerize-nodejs-web-applications-with-docker/
# https://nodejs.org/en/docs/guides/nodejs-docker-webapp/
FROM node:18-alpine
# RUN apk add dumb-init
ENV NODE_ENV production
ENV NODE_PATH /app
WORKDIR /app
ADD . ./
# RUN npm install  <- tried this, it didn't work
RUN npm ci --only=production
RUN npm run build

USER node

EXPOSE 3000

ENTRYPOINT ["npm", "start"]

# silence annoying snyk message by running this in bash
# export DOCKER_SCAN_SUGGEST=false
#