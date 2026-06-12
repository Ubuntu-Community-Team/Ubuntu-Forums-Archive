---
title: "Connection Reset By Peer"
date: 2009-01-17
forum: General Help
---

### Post by jaishreepadma on 2009-01-17
Hi ALL,
Actually Client is sending data to the  Tomcat apache server.
To send data
1.Create TCP Socket
2.In the TCP socket with sending request with HTTP/1.1
3. I am trying to send text/xml data nearly 15 KBytes.
4.Connections is rest by the server ( It send the RST-Reset) after 5 HTTP request
5..My requirement is to send atleast 64 Kbytes in a TCP socket

It is possible?
My doubt , why Server  is sending  Reset message??.
is it b'caz of
 1.Time out ?
2.can we send only 5 HTTP request in a TCP socket

---

