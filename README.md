# 2a_Stop_and_Wait_Protocol

## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
#server.py
```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)

print("Waiting for connection...")
conn, addr = s.accept()
print("Connected to", addr)

while True:
    data = conn.recv(1024).decode()
    if not data:
        break

    print("Frame received:", data)
    conn.send("ACK".encode())

conn.close()
```
#client.py
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

n = int(input("Enter number of frames: "))

for i in range(n):
    msg = input("Enter frame: ")
    s.send(msg.encode())

    ack = s.recv(1024).decode()
    print("Received:", ack)

s.close()
```
## OUTPUT
<img width="1917" height="1023" alt="Screenshot 2026-11-03 134635" src="https://github.com/user-attachments/assets/c1dde4cb-ec61-4b05-a602-e9653b42d18c" />


<img width="1917" height="1021" alt="Screenshot 2026-11-03 134652" src="https://github.com/user-attachments/assets/0b35c1a0-0f6b-4ef1-9835-52d15bb64a68" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
