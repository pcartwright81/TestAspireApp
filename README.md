# TestAspireApp

A .NET Aspire application demonstrating cloud-native application development with distributed services, service discovery, and telemetry.

## Overview

TestAspireApp is built using [.NET Aspire](https://learn.microsoft.com/en-us/dotnet/aspire/), Microsoft's opinionated stack for building observable, production-ready cloud-native applications. This project showcases a microservices architecture with a web frontend and API backend service.

## Project Structure

- **TestAspireApp.AppHost** - The orchestrator project that manages service discovery and configuration
- **TestAspireApp.ApiService** - RESTful API service providing weather forecast data
- **TestAspireApp.Web** - Web frontend application
- **TestAspireApp.ServiceDefaults** - Shared service configuration and defaults
- **TestAspireApp.Tests** - Unit and integration tests

## Features

- ✨ Weather forecast API endpoint
- 🔍 Built-in service discovery
- 📊 OpenAPI/Swagger integration for API documentation
- 🎯 Aspire dashboard for observability
- 🏗️ Modern minimal API architecture
- 🧪 Test project included

## Prerequisites

- [.NET 9.0 SDK](https://dotnet.microsoft.com/download/dotnet/9.0) or later
- [.NET Aspire workload](https://learn.microsoft.com/en-us/dotnet/aspire/fundamentals/setup-tooling)
- Visual Studio 2022 (17.9+) or JetBrains Rider

### Installing .NET Aspire Workload

```bash
dotnet workload install aspire
```

## Getting Started

### Running the Application

1. Clone the repository:
   ```bash
   git clone https://github.com/pcartwright81/TestAspireApp.git
   cd TestAspireApp
   ```

2. Run the AppHost project:
   ```bash
   dotnet run --project TestAspireApp.AppHost
   ```

3. The Aspire dashboard will open automatically, showing all services and their health status

4. Access the weather forecast API:
   ```
   GET http://localhost:<port>/weatherforecast
   ```

### API Endpoints

#### Get Weather Forecast
Returns a 5-day weather forecast with temperature data.

**Endpoint:** `GET /weatherforecast`

**Response:**
```json
[
  {
    "date": "2024-12-08",
    "temperatureC": 15,
    "temperatureF": 59,
    "summary": "Mild"
  }
]
```

## Key Code Highlight

The `WeatherForecast` record demonstrates modern C# features with a computed property for temperature conversion:

```csharp
public record WeatherForecast(DateOnly Date, int TemperatureC, string? Summary)
{
    public int TemperatureF => 32 + (int)(TemperatureC / 0.5556);
}
```

This record type provides:
- **Immutable data structure** with positional parameters
- **Computed property** (`TemperatureF`) that converts Celsius to Fahrenheit
- **Nullable reference type** for the `Summary` property
- **Concise syntax** using C# 9.0+ record types

## Testing

Run the test suite:

```bash
dotnet test
```

## Development

### Using Visual Studio 2022
1. Open `TestAspireApp.slnx`
2. Set `TestAspireApp.AppHost` as the startup project
3. Press F5 to run with debugging

### Using .NET CLI
```bash
# Build the solution
dotnet build

# Run tests
dotnet test

# Run with watch mode for development
dotnet watch --project TestAspireApp.AppHost
```

## Configuration

Application settings can be modified in:
- `appsettings.json` - Default configuration
- `appsettings.Development.json` - Development environment overrides

## Observability

The Aspire dashboard provides:
- Service health monitoring
- Distributed tracing
- Logs aggregation
- Metrics visualization

Access the dashboard at `http://localhost:15888` when running the application.

## Technologies Used

- .NET 9.0
- ASP.NET Core Minimal APIs
- .NET Aspire
- OpenAPI (Swagger)
- C# 12 Records

## License

This project is licensed under the MIT License - see the [LICENSE.txt](LICENSE.txt) file for details.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Resources

- [.NET Aspire Documentation](https://learn.microsoft.com/en-us/dotnet/aspire/)
- [ASP.NET Core Documentation](https://learn.microsoft.com/en-us/aspnet/core/)
- [OpenAPI Specification](https://www.openapis.org/)

## Author

Patrick Cartwright ([@pcartwright81](https://github.com/pcartwright81))
