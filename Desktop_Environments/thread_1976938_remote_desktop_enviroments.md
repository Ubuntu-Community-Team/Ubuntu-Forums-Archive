---
title: "remote desktop enviroments"
date: 2012-05-09
forum: Desktop Environments
---

### Post by Cycorp on 2012-05-09
My system is Ubuntu 11.10 and have installed gnome.
 
When I login at the console I can set my desktop enviroment as gnome. 
How do I do this when I remote in ?
 
When I try to remote in using vnc to the console I am getting errors if the console is not currently logged in.
 
How do I switch session if multiple id's are logged in at the same time ?
 
thanks

---

### Post by Rokel on 2012-09-19
In Ubuntu a user enables VNC to his sessions by enabling the VINO server to start listening when he is logged in. 

If nobody is logged in you could SSH to the box as root, start x11vnc like this:

x11vnc -nopw -once -auth /var/lib/lightdm/.Xauthority -display :0

(not secure on a public lan!!)

The  VNC session will get the the lightdm login screen where you enter your username and password and select the session type you want (kde, gnome etc) 

If you use "ssh -L5900:localhost:5900  user@linuxbox" you forward the port to your own machine, so on that machine you do "vncviewer localhost:5900" 

(notice the 5900 might change to 5901, 5902, depending on concurrent sessions)

use x11vnc -auth guess and x11vnc -auth find to find your proper display managers authorization cookie key file.

---

### Post by markbl on 2012-09-19
> **Rokel said:**
> 
x11vnc -nopw -once -auth /var/lib/lightdm/.Xauthority -display :0

(not secure on a public lan!!)

Rokel, note you are accessing that vnc session via your ssh tunnel so there is no need to open up the X port to the local network. So therefore just add a "-localhost" to the above x11vnc command and then only your ssh connection can access it, and then no need for that warning you give above.

---

