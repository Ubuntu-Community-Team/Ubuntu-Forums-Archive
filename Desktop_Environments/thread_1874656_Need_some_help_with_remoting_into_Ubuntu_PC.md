---
title: "Need some help with remoting into Ubuntu PC"
date: 2011-11-03
forum: Desktop Environments
---

### Post by rollin77 on 2011-11-03
I have a PC running Ubuntu 10.04 (32 bit) located in my garage.  I want to be able to remote into this PC from another PC running Ubuntu inside the house.

I know I need to setup some sort of VNC program, but as far as I can tell I've done that but when I remote in I only get a command prompt on the remote PC instead of a graphical user interface which is what I need.  I've already read through most of the VNC links [including this one]("https://help.ubuntu.com/community/VNC"), but nothing really seems to make sense.  I need something in layman's terms on how to set this up.  

-What programs should I use on the remote PC in the garage, and how do I set those up?
-What programs should I use from the PC inside the house to connect to the remote PC?

I'm not interested in connecting from the internet, just another Ubuntu PC on the same network.

---

### Post by Script Warlock on 2011-11-03
you can use vnc, teamviewer or nx machine... ubuntu has a remote desktop viewer.

---

### Post by rollin77 on 2011-11-03
So how do I do that?  Please explain the steps not just the programs I need ot use.  I've already installed a vnc server program on the remote Ubuntu PC but I'm not getting a graphical interface when I remote in, only a command prompt.

---

### Post by Script Warlock on 2011-11-03
if you want to use teamviewer just install it from their site and launch which also displays an id and password.

---

### Post by rollin77 on 2011-11-03
Teamviewer is slow and useless, I'd rather stick with something using VNC.

---

### Post by Script Warlock on 2011-11-03
1. (client) locate Desktop Sharing> set your preference
2. check port thru terminal: netstat -anltp | grep "LISTEN" -- 5900 should be up and listening
3. port forward the router if your using one port# 5900
4. (server) locate Remote Desktop Viewer> connect> VNC> host ip 192.168.x.x::5900> set options if you prefer to and press CONNECT.

---

