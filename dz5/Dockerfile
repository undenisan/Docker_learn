FROM mcr.microsoft.com/dotnet/sdk:6.0-jammy AS build
WORKDIR /work
COPY net/ /work/
RUN dotnet build WebApplication_DIT_Docker.sln

FROM mcr.microsoft.com/dotnet/aspnet:6.0-jammy
LABEL version="1.0"
EXPOSE 8080
WORKDIR /app
COPY --from=build /work/WebApplication_DIT_Docker/bin/Debug/net:6.0/*.dll /app/
COPY --from=build /work/WebApplication_DIT_Docker/bin/Debug/net:6.0/*.json /app/
USER 9000:9000
ENTRYPOINT ["dotnet", "WebApplication_DIT_Docker.dll"]
