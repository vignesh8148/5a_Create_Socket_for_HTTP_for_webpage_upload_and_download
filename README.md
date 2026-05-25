# 5a_Create_Socket_for_HTTP_for_webpage_upload_and_download
## AIM :
To write a PYTHON program for socket for HTTP for web page upload and download
## Algorithm

1.Start the program.
<BR>
2.Get the frame size from the user
<BR>
3.To create the frame based on the user request.
<BR>
4.To send frames to server from the client side.
<BR>
5.If your frames reach the server it will send ACK signal to client otherwise it will send NACK signal to client.
<BR>
6.Stop the program
<BR>
## Program 
SERVER.PY
```

import socket

server = socket.socket()

server.bind(('localhost', 8080))

server.listen(1)

print("Server waiting...")

conn, addr = server.accept()

print("Connected by", addr)

request = conn.recv(1024).decode()

print("Client Request:")
print(request)

response = """HTTP/1.1 200 OK

<html>
<head>
<title>HTTP Socket</title>
</head>

<body>
<h1>HTTP Socket Program Executed Successfully</h1>
</body>
</html>
"""

conn.send(response.encode())

conn.close()
server.close()
```
CLIENT.PY
```

import socket

client = socket.socket()

client.connect(('localhost', 8080))

request = "GET / HTTP/1.1\r\nHost: localhost\r\n\r\n"

client.send(request.encode())

response = client.recv(4096).decode()

print("Server Response:")
print(response)

client.close()
```
## OUTPUT
<img width="1063" height="391" alt="{8B22C36B-6F74-4F74-A661-14C50FEF9E53}" src="https://github.com/user-attachments/assets/51f1421e-53a2-4bf8-ab67-154fb2e7011f" />


## Result
Thus the socket for HTTP for web page upload and download created and Executed
