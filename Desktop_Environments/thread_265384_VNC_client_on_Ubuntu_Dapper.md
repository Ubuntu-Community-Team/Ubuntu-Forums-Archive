---
title: "VNC client on Ubuntu Dapper"
date: 2006-09-25
forum: Desktop Environments
---

### Post by MacPC on 2006-09-25
Hi,

Can someone walk me throught the steps needed to set up a VNC client on Ubuntu?

MacPC

---

### Post by Mr Frosti on 2006-09-25
A VNC client is easy. You have two options, one being a GUI client and the other being a terminal based client. 

If you are new to VNC, I recommend using a GUI. For Gnome, try the "Terminal Services Client". This will allow you to connect to VNC, or Windows Remote Desktop. If you are using KDE, give Krd a try. Again, this gives the option of VNC, or Windows Remote Desktop.

In terms of connecting the client to an existing VNC server, just type in the IP address. This is the only required field other than authentication (username, password). 

If this does not connect, the most common cause if a firewall blocking the port that VNC uses. Typically, VNC servers will use port "5900" unless otherwise specified. Check with the server.

If you still can't connect, include any error messages below.

---

### Post by D10 on 2006-09-25
> **MacPC said:**
> Hi,

Can someone walk me throught the steps needed to set up a VNC client on Ubuntu?

MacPC

If you are connecting to a windows machine via VNC you might just need a browser with java. Most default installs of VNC on Windows also installs a http/java  server. If you have java installed on your linux machine just point your browser to [http://0.0.0.0:5800](http://0.0.0.0:5800) (where 0.0.0.0 is the IP or name of the machine you want to connect to port 5800 is default)

If you are connecting a new windows version of VNC (i.e Ultra VNC 1.0.2)that uses windows authentication I have found you can only connect using the browser java viewer. There might be a native linux client I just haven't heard of it.

---

### Post by ogu on 2006-09-26
"Terminal Server Client" is quite simple.

You might also want to check the VNC version on the other side. For example, i had a newer version of Real VNC on my Windows PC and i couldn't connect to it because of version incompatibilities so i had to use "legacy mode" on my server. So be aware of those kind of things :).

---

### Post by expatCM on 2006-09-26
perhaps this helps?

[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

---

