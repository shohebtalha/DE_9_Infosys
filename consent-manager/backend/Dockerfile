# Build only Consent Manager from this directory. The application has no
# Maven dependency on the repository-level aggregator or either college app.
FROM maven:3.9.6-eclipse-temurin-17 AS build
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn -B clean package -DskipTests

FROM eclipse-temurin:17-jre-alpine
WORKDIR /app
COPY --from=build /app/target/*.jar app.jar

ENV PORT=8095
EXPOSE 8095
ENTRYPOINT ["java", "-jar", "app.jar"]
