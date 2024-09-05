# Use the .NET SDK image to build the application
FROM mcr.microsoft.com/dotnet/sdk:7.0 as build

WORKDIR /source
COPY *.csproj .
RUN dotnet restore

COPY . .
RUN dotnet publish -c release -o /app --no-restore

# Use the .NET runtime image to run the application
FROM mcr.microsoft.com/dotnet/runtime:7.0
WORKDIR /app
COPY --from=build /app .
ENTRYPOINT ["dotnet", "Worker.dll"]
