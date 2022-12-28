#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app
EXPOSE 80

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
COPY ["TraxAPI/TraxAPI.csproj", "TraxAPI/"]
COPY ["TraxAPI.Business/TraxAPI.Business.csproj", "TraxAPI.Business/"]
COPY ["InforWorkOrder/InforWorkOrder.csproj", "InforWorkOrder/"]
COPY ["TraxAPI.Helper/TraxAPI.Helper.csproj", "TraxAPI.Helper/"]
COPY ["TraxAPI.Entities/TraxAPI.Entities.csproj", "TraxAPI.Entities/"]
COPY ["TraxAPI.Reporting/TraxAPI.Reporting.csproj", "TraxAPI.Reporting/"]
RUN dotnet restore "TraxAPI/TraxAPI.csproj"
COPY . .
WORKDIR "/src/TraxAPI"
RUN dotnet build "TraxAPI.csproj" -c Release -o /app/build

