## Project Overview

This project connects to the realtime route of Pocketbase to determine whether the server is online or not. If the server is disconnected, the client is restarted. The following JavaScript code is used to connect to the realtime route of Pocketbase:

``` javascript
const evtSource = new EventSource("/api/realtime");

evtSource.onerror = function (event) {
  setTimeout(() => {
    window.location.reload();
  }, 500);
};

window.addEventListener("beforeunload", function (event) {
  evtSource.close();
});
```

## Getting Started

To get started with this project, please follow these steps:

1. Clone the repository by running the following command:

``` shell
git clone https://github.com/somenoe/pocketbase-client-hot-reload.git
```

2. Change the directory to the project directory:

``` shell
cd pocketbase-client-hot-reload
```

3. Install the dependencies:

``` shell 
go mod tidy
``` 

## Hot Reload

To enable hot reload, you can use [air](https://github.com/cosmtrek/air), a live-reloading tool for Go applications. To use air, follow these steps:

1. Install air:

``` shell
go install github.com/cosmtrek/air@latest
```

2. Run air:

``` shell
air
```

This will start the application with hot reload enabled. Any changes you make to the code will be automatically reloaded by air.