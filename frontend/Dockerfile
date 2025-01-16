# Use official Node.js image as a build environment
FROM node:16 AS build

WORKDIR /app

# Install dependencies
COPY package.json ./
COPY package-lock.json ./
RUN npm install

# Copy source code and build the app
COPY . ./
RUN npm run build

# Use Nginx to serve the built files
FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
