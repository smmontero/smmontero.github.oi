<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SERVICIOS WEB</title>
    <link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css" />
    <style>
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            background-color: #1e3d58; /* Fondo azul */
            color: white;
            overflow: hidden; /* Elimina la barra de desplazamiento */
        }
        header {
            background-color: #333;
            color: white;
            padding: 20px;
            font-size: 1.5em;
        }
        nav {
            background-color: #007bff; /* Azul más brillante */
            color: white;
            padding: 15px;
            display: flex;
            justify-content: space-around;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
        }
        nav a {
            color: white;
            text-decoration: none;
            padding: 10px 15px;
            border-radius: 5px;
            transition: background-color 0.3s;
        }
        nav a:hover {
            background-color: #0056b3; /* Azul más oscuro */
        }
        section {
            padding: 20px;
            margin: 20px;
            background-color: #fff;
            color: #333;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            display: none; /* Ocultamos todas las secciones por defecto */
        }
        h2 {
            color: #007bff; /* Azul */
        }
        #map {
            height: 400px;
            width: 100%;
            border-radius: 8px;
            margin-top: 10px;
        }
        input[type="text"], button {
            padding: 10px;
            margin: 5px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
            width: calc(100% - 22px);
        }
        button {
            background-color: #007bff; /* Azul */
            color: white;
            border: none;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        button:hover {
            background-color: #0056b3; /* Azul más oscuro */
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 10px;
        }
        th, td {
            padding: 10px;
            text-align: left;
            border-bottom: 1px solid #ddd;
        }
        th {
            background-color: #007bff; /* Azul */
            color: white;
        }
        tr:hover {
            background-color: #f1f1f1;
        }
        #formResponse {
            margin-top: 10px;
            color: #007bff; /* Azul */
        }
        /* Estilo adicional para mejorar la apariencia */
        input[type="text"] {
            border: 1px solid #007bff; /* Azul */
        }
        input[type="text"]:focus {
            border-color: #0056b3; /* Azul más oscuro */
            outline: none;
        }
        /* Estilo para el iframe */
        iframe {
            border: 2px solid #007bff; /* Azul */
            border-radius: 8px;
        }
    </style>
</head>
<body>
    <header>
        SERVICIOS WEB
    </header>
    <nav>
        <a href="#" onclick="showSection('ubicacion')">Ubicación</a>
        <a href="#" onclick="showSection('clima')">Clima</a>
        <a href="#" onclick="showSection('registro')">Registro</a>
        <a href="#" onclick="showSection('multimedia')">Multimedia</a>
    </nav>

    <section id="ubicacion">
        <h2>Tu Ubicación</h2>
        <button onclick="getLocation()">Obtener mi ubicación</button>
        <div id="location"></div>
        <div id="map"></div>
    </section>

    <section id="clima">
        <h2>Consulta del Clima</h2>
        <input type="text" id="city" placeholder="Ingresa una ciudad">
        <button onclick="getWeatherByCity()">Consultar Clima</button>
        <div id="weatherResult"></div>
        <table id="weatherTable" style="display: none;">
            <thead>
                <tr>
                    <th>Ciudad</th>
                    <th>País</th>
                    <th>Temperatura (°C)</th>
                    <th>Descripción</th>
                    <th>Humedad (%)</th>
                    <th>Velocidad del Viento (m/s)</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td id="cityName"></td>
                    <td id="countryName"></td>
                    <td id="temperature"></td>
                    <td id="weatherDescription"></td>
                    <td id="humidity"></td>
                    <td id="windSpeed"></td>
                </tr>
            </tbody>
        </table>
    </section>

    <section id="registro">
        <h2>Registro de Usuario</h2>
        <form id="registrationForm" onsubmit="submitForm(event)">
            <label for="username">Nombre de Usuario:</label>
            <input type="text" id="username" required>
            <br>
            <label for="matricula">Matrícula:</label>
            <input type="text" id="matricula" required>
            <br>
            <label for="archivo">Seleccionar Archivo:</label>
            <input type="file" id="archivo" required>
            <button type="submit">Registrar</button>
        </form>
        <div id="formResponse"></div>
        <h3>Registros:</h3>
        <table>
            <thead>
                <tr>
                    <th>Nombre de Usuario</th>
                    <th>Matrícula</th>
                    <th>Archivo</th>
                </tr>
            </thead>
            <tbody id="dataTableBody"></tbody>
        </table>
    </section>

    <section id="multimedia">
        <h2>Contenido Multimedia</h2>
        <h3>Video</h3>
        <video width="560" height="315" controls>
            <source src="video.mp4" type="video/mp4">
            Tu navegador no soporta la etiqueta de video.
        </video>
        <h3>Descargar Imagen</h3>
        <a href="l.png" download>Descargar Imagen</a>
    </section>

    <div class="contador">
        <h2>Contador de Visitas</h2>
        <div id="sfc2en1kmw15ng7dhbx8h3krck4q8k5yy5f"></div>
        <script type="text/javascript" src="https://counter6.optistats.ovh/private/counter.js?c=2en1kmw15ng7dhbx8h3krck4q8k5yy5f&down=async" async></script>
        <noscript>
            <a href="https://www.contadorvisitasgratis.com" title="contador de visitas para web">
                <img src="https://counter6.optistats.ovh/private/contadorvisitasgratis.php?c=2en1kmw15ng7dhbx8h3krck4q8k5yy5f" border="0" title="contador de visitas para web" alt="contador de visitas para web">
            </a>
        </noscript>
    </div>

    <script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>
    <script>
        let map;

        function initMap() {
            map = L.map('map').setView([0, 0], 2); // Inicializa el mapa en una vista global

            L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
                maxZoom: 19,
                attribution: '© OpenStreetMap'
            }).addTo(map);
        }

        function showSection(sectionId) {
            const sections = document.querySelectorAll('section');
            sections.forEach(section => {
                section.style.display = 'none'; // Oculta todas las secciones
            });
            document.getElementById(sectionId).style.display = 'block'; // Muestra la sección seleccionada
        }

        window.onload = function() {
            initMap();
            showSection('ubicacion'); // Muestra la sección de ubicación al cargar la página
        };
    </script>
</body>
</html>

