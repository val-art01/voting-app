# FROM bitnami/dotnet:latest 
# As build
FROM mcr.microsoft.com/dotnet/sdk:7.0 As build
WORKDIR /usr/src/app
COPY *.csproj .
RUN dotnet restore
COPY . .
RUN dotnet publish -c release --self-contained false --no-restore

FROM mcr.microsoft.com/dotnet/runtime:7.0
WORKDIR /usr/src/app
COPY --from=build /usr/src/app .
CMD ["dotnet", "bin/release/net7.0/Worker.dll"]
# , "--postgres-host", "postgres"
# FROM bitnami/dotnet-sdk:latest