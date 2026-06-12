---
title: "networking...what is the VNCviewer server name or ip address?"
date: 2005-12-14
forum: General Help
---

### Post by dpmaxey on 2005-12-14
when it says for me to type in the little tiny tiny window when i want to connect to my computer at home from school, what do i type? is it the server's ip address? or is it the server's host name? i'm not sure, it doesn't really tell me what to put.
:confused:

[SIZE=4]:???:~kawika~:???:[/SIZE]

---

### Post by inhetep on 2005-12-14
U will need the exact ip address of your computer at home. If you don't have a permanent IP at home, it will be a little bit problematic.
It might help using dyndns 
```
http://www.dyndns.com/
```
and if u have a router u need forward it to the computer in question.

---

### Post by localzuk on 2005-12-14
[QUOTE=inhetep]if u have a router u need forward it to the computer in question.[/QUOTE]

To expand on this point:

When connecting to a computer from a remote location via VNC you will likely end up using a port number such as 5900. If you use a router, you will be trying to access the port on the router rather than the computer you wish to access.

The way to solve this is to, via the router admin software/pages, set up 'Port Forwarding'. This will allow you to tell the router to forward all data that is received on the port 5900 to the ip address (internal IP - not internet/external IP) of the computer you want.

---

### Post by 0okami on 2005-12-14
also, if you are using ubuntu linux elsewhere, you can connect to the other machine using vncviwer. 

in a terminal, type: 
vncviewer xxx.xxx.xxx.xxx:5900

where xxx is your server IP (the ip to the machine you are connecting to)
if ports are set right, it will ask for pw if you set it (i hope you did)... and then you can connect. 

:) 

works really good on fast connections.
Fantastic for remote assistance.

---

