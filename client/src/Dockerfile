# Etapa 1: build de React
FROM node:20-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .

RUN npm run build

# Etapa 2: Servir con Nginx
FROM nginx:alpine
# Copiar la build generada al directorio que Nginx sirve
COPY --from=build /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
