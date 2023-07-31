# Build stage
FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
WORKDIR /source

# Copy the project file and restore dependencies
COPY PoojaStores.csproj ./
RUN dotnet restore

# Copy and publish the app and libraries
COPY . ./
RUN dotnet publish -c release -o /app --no-restore

# Final stage/image
FROM mcr.microsoft.com/dotnet/aspnet:3.1
WORKDIR /app
COPY --from=build /app .
ENTRYPOINT ["dotnet", "PoojaStores.dll"]



