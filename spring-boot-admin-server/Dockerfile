FROM eclipse-temurin:17-jre

ENV APP_NAME spring-boot-admin-server
ENV DEFAULT_JVM_OPTS="$DEFAULT_JVM_OPTS -Duser.timezone=GMT-3"
ENV DEFAULT_JVM_OPTS="$DEFAULT_JVM_OPTS -Djava.io.tmpdir=/opt/rest-services/temp"
ENV DEFAULT_JVM_OPTS="$DEFAULT_JVM_OPTS -XX:+UseG1GC"
ENV DEFAULT_JVM_OPTS="$DEFAULT_JVM_OPTS -XX:+UseStringDeduplication"

ENV DEFAULT_SPRING_OPTS="$DEFAULT_SPRING_OPTS --management.endpoints.web.exposure.include=*"
ENV DEFAULT_SPRING_OPTS="$DEFAULT_SPRING_OPTS --management.info.java.enabled=true"
ENV DEFAULT_SPRING_OPTS="$DEFAULT_SPRING_OPTS --management.info.build.enabled=true"
ENV DEFAULT_SPRING_OPTS="$DEFAULT_SPRING_OPTS --management.info.env.enabled=true"
ENV DEFAULT_SPRING_OPTS="$DEFAULT_SPRING_OPTS --management.metrics.enable.jvm=false"
ENV DEFAULT_SPRING_OPTS="$DEFAULT_SPRING_OPTS --management.metrics.export.atlas.enabled=false"
ENV DEFAULT_SPRING_OPTS="$DEFAULT_SPRING_OPTS --management.health.consul.enabled=false"
ENV DEFAULT_SPRING_OPTS="$DEFAULT_SPRING_OPTS --management.endpoint.health.probes.enabled=true"

ENV DEFAULT_SPRING_OPTS="$DEFAULT_SPRING_OPTS --spring.cloud.consul.host=consul"
ENV DEFAULT_SPRING_OPTS="$DEFAULT_SPRING_OPTS --spring.cloud.consul.port=8500"
ENV DEFAULT_SPRING_OPTS="$DEFAULT_SPRING_OPTS --spring.cloud.consul.discovery.enabled=true"
ENV DEFAULT_SPRING_OPTS="$DEFAULT_SPRING_OPTS --spring.cloud.consul.discovery.register=true"

ENV DEFAULT_SPRING_OPTS="$DEFAULT_SPRING_OPTS --spring.cloud.consul.discovery.prefer-ip-address=true"
ENV DEFAULT_SPRING_OPTS="$DEFAULT_SPRING_OPTS --spring.cloud.consul.discovery.deregister=false"
ENV DEFAULT_SPRING_OPTS="$DEFAULT_SPRING_OPTS --spring.cloud.consul.discovery.health-check-critical-timeout=1440m"
	

COPY ./target/${APP_NAME}.jar  /app/${APP_NAME}.jar


WORKDIR /app


#CMD java -jar ${APP_NAME}.jar

#CMD java -jar ${APP_NAME}.jar $DEFAULT_SPRING_OPTS
CMD java -jar ${APP_NAME}.jar --spring.cloud.consul.discovery.ip-address=$(hostname -i)
#CMD java $DEFAULT_JVM_OPTS -Ddd.service=$(basename ./target/*.*ar) -jar $(basename ./target/*.*ar) $DEFAULT_SPRING_OPTS --spring.cloud.consul.discovery.ip-address=$(hostname -i | awk '{print $1}')

EXPOSE 8080/tcp