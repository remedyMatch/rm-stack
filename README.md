## Kickstart

Stack ausführen:

`docker-compose up --force-recreate --build`

Stack updaten:

`docker-compose pull`

Stack vollständig zurücksetzen und aktualisieren:

`docker-compose rm`

`docker volume rm rm-stack_db-data`

`docker-compose pull`

`docker-compose up --force-recreate --build`

## Services

Folgende Services werden auf localhost bereitgestellt. Hier muss darauf geachtet werden, dass der Port nicht schon
durch eine Anwendung auf dem Host System blockiert wird, da die Ports alle auf dem Host System gebunden werden müssen.

| Port | Beschreibung       |
|------|--------------------|
| 3306 | MySQL              |
| 8008 | Reverse Proxy      |

## Reverse Proxy Exports

Der Reverse Proxy exportiert alle Services auf einem einzelnen HTTP Host, damit diese reibungslos

miteinander kommunizieren können (Stichwörter CORS / JWT Origin)

### Keycloak

Admin Console

`http://localhost:8008/auth/admin/`

User: `admin`

Passwort: `admin`

### Camunda

`http://localhost:8008/engine/app/welcome/default/`

User: `admin`

Passwort: `admin`


### RemedyMatch Frontend

`http://localhost:8008/app/`

User: `test_bedarf`

Passwort: `G3h31m`


User: `test_spender`

Passwort: `G3h31m`


## Komponenten entwickeln

### React frontend

* Local development server starten mit `yarn run start`

* `nginx.conf` editieren, `/app/` route `http://host.docker.internal:3000/app/` als proxy verwenden

* Stack neu starten
