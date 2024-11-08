# TorontoWeather

The `TorontoWeather` project contains a `WeatherService` class that fetches weather information for Toronto using the Open-Meteo API. This service allows you to get the daily maximum temperatures for Toronto and can be expanded to include additional weather data.

## Features

- Fetches the weather data asynchronously using the Open-Meteo API.
- Extracts daily maximum temperatures for Toronto.
- Uses the `HttpClient` class to make HTTP requests and handle responses.
- Parses JSON responses with `Newtonsoft.Json` (JObject) for easier manipulation.

## Requirements

- .NET 5 or later.
- Internet access to fetch data from the Open-Meteo API.
- [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/) for JSON parsing.

## Getting Started

### Install Dependencies

Before using the `WeatherService` class, ensure that your project includes the necessary dependencies. Install `Newtonsoft.Json` via NuGet:

```bash
dotnet add package Newtonsoft.Json


### Example Usage

using System;
using System.Threading.Tasks;

namespace TorontoWeather
{
    class Program
    {
        static async Task Main(string[] args)
        {
            var weatherService = new WeatherService();
            var weatherData = await weatherService.GetTorontoWeatherAsync();

            Console.WriteLine($"Daily Maximum Temperatures for Toronto: {weatherData}");
        }
    }
}

### How It Works
WeatherService Constructor: Initializes the HttpClient used to send HTTP requests.

GetTorontoWeatherAsync() Method:

Constructs the URL with the appropriate query parameters for latitude, longitude, and the required data (daily max temperature and timezone).
Sends an asynchronous GET request to fetch weather data in JSON format.
Returns a string containing the maximum temperatures for each day.
ExtractMaxTemperatures() Method:

Extracts the daily maximum temperatures from the parsed JSON response.
Returns an array of temperatures in Celsius.


### Sample Output
Daily Maximum Temperatures for Toronto: 12.3, 13.5, 14.6, 15.2, 16.1

### API Details
The service uses the Open-Meteo API to fetch weather data. Specifically, it requests:

latitude: 43.7 (Toronto's latitude).
longitude: -79.42 (Toronto's longitude).
daily: temperature_2m_max (daily maximum temperature).
timezone: America/Toronto (to get the weather data in the Toronto timezone).

### Contributing
Contributions are welcome! If you have suggestions or improvements for this service, feel free to fork this repository and submit a pull request.

### License
This project is licensed under the MIT License - see the LICENSE file for details.


### This `README.md` provides an overview of how the `WeatherService` works, its functionality, and how to use it in a .NET Core application. Let me know if you need further adjustments!
