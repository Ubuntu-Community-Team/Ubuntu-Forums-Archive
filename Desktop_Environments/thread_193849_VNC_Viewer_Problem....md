---
title: "VNC Viewer Problem..."
date: 2006-06-10
forum: Desktop Environments
---

### Post by nocloud on 2006-06-10
linux is working for me fine, but unless i get this vnc problem fixed, i'm going to have to go back to windows.....

i installed xvnc4viewer, when i try to connect to my webserver, i get this:

Sat Jun 10 12:45:19 2006
 CConn:       connected to host xxxxxxxxxxxxxx port 5900
 CConnection: Server supports RFB protocol version 4.0
 CConnection: Using RFB protocol version 3.8
 CConnection: No matching security types
 main:        No matching security types

does anybody know how i can fix that?  i really really have to be able to connect to the server through vnc....

---

### Post by FizDev on 2006-06-10
Don't know about xvnc4viewer, but you could try with tightvnc
To install it (client) :
```
sudo apt-get install xtightvncviewer
```

---

### Post by nocloud on 2006-06-10
with tightviewer, i get this message that says the client is vnc version 3.3 while the server is version 4 and that it cannot connect because the versions are different

---

### Post by harisund on 2006-06-12
I am not sure, but maybe you can give a password for your server and try again?

---

