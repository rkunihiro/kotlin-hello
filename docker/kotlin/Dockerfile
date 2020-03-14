FROM openjdk:13-alpine AS installer
RUN apk add curl zip \
 && cd /opt \
 && curl -L -o kotlin-compiler-1.3.70.zip https://github.com/JetBrains/kotlin/releases/download/v1.3.70/kotlin-compiler-1.3.70.zip \
 && unzip kotlin-compiler-1.3.70.zip \
 && curl -L -o gradle-6.2.2-bin.zip https://services.gradle.org/distributions/gradle-6.2.2-bin.zip \
 && unzip gradle-6.2.2-bin.zip \
 && mv gradle-6.2.2 gradle

FROM openjdk:13-alpine AS kotlin
COPY --from=installer /opt/kotlinc /opt/kotlinc
COPY --from=installer /opt/gradle /opt/gradle
ENV PATH $PATH:/opt/kotlinc/bin:/opt/gradle/bin
RUN apk add bash
