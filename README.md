# conversate

## Description

A js client library to talk to conversate server (https://github.com/nyelnizy/conversate.git)

## Install
Simply download and add to your js project

## Connecting to the server
The connection has to be made when the app starts, if you are using vue js, the main.js file will be a good place.
```bash
import { ConnectXOne } from "./cx_client";

const cs = new ConversateServer()
cs.connect("ws://127.0.0.1:6001", 2, "token")
```
The connect method has 3 parameters. 1) The server url, 
2) The total number of times to retry when connection drops, 
3) The localstorage key name for the jwt token.

Note: Total tries is optional, if its not set the client will retry until connection is re established.
Also token key is optional, by default the client uses token as the token key to lookup token in localstorage.

## Sending a request
An instance of the client is available on the window object.
```bash
window.cs.converse("get-users", (response) => {
    console.log(response)
}, (error) => {
    console.log(error)
},{data:"is optional"})
```