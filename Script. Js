const apiKey = 'YOUR_API_KEY'; // Replace with your actual API key from OpenWeather

async function getWeather() {
  const city = document.getElementById('city-input').value;

  if (!city) {
    alert('Please enter a city name');
    return;
  }

  const apiUrl = `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}&units=metric`;

  try {
    const response = await fetch(apiUrl);

    if (!response.ok) {
      throw new Error(`City not found: ${response.statusText}`);
    }

    const data = await response.json();
    displayWeather(data);
  } catch (error) {
    document.getElementById('weather-info').innerHTML = `<p>${error.message}</p>`;
  }
}

function displayWeather(data) {
  const weatherInfo = document.getElementById('weather-info');
  const { name, main, weather, wind } = data;
  
  weatherInfo.innerHTML = `
    <h2>Weather in ${name}</h2>
    <p><strong>Temperature:</strong> ${main.temp} °C</p>
    <p><strong>Humidity:</strong> ${main.humidity}%</p>
    <p><strong>Wind Speed:</strong> ${wind.speed} m/s</p>
    <p><strong>Condition:</strong> ${weather[0].description}</p>
    <img src="https://openweathermap.org/img/wn/${weather[0].icon}@2x.png" alt="Weather icon" />
  `;
}
