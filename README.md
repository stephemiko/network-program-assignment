Client.py README
The client program takes two command line arguments: the hostname and port number of the server it wants to connect to.

It creates a UDP socket using socket.socket(socket.AF_INET, socket.SOCK_DGRAM).

It then sends 10 'PING' messages to the server using a loop. The message is converted to bytes with message = 'PING'.encode().

After sending each 'PING' message, it waits for a response from the server. It sets a timeout of 1 second for the response using client_socket.settimeout(1).

If it receives a response within the timeout period, it prints 'received <response>'. Otherwise, it prints 'Timed Out'.

Finally, it closes the socket with client_socket.close().

Server.py README
The server program takes one command line argument: the port number it should listen on.

It creates a UDP socket using socket.socket(socket.AF_INET, socket.SOCK_DGRAM).

It binds the socket to the specified port on localhost using server_socket.bind(('localhost', port)).

It enters an infinite loop to continuously receive messages from clients.

When a message is received, it prints '[client] : <message>'.

It then randomly decides whether to drop the packet or send back a 'PONG' response. It simulates dropping packets 30% of the time using if random.random() < 0.3.

If the packet is not dropped, it sends back a 'PONG' response to the client using server_socket.sendto('PONG'.encode(), address).
