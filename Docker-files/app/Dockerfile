FROM maven:3.9.9-eclipse-temurin-21-jammy AS builder
LABEL "Author"="Van Luong"
COPY . vprofile-project/
RUN cd vprofile-project && mvn install

FROM tomcat:10.1.52-jdk21-temurin-jammy
LABEL "Author"="Van Luong"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=builder vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war
EXPOSE 8080
CMD ["catalina.sh", "run"]