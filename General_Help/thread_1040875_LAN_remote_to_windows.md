---
title: "LAN remote to windows"
date: 2009-01-16
forum: General Help
---

### Post by limanoit on 2009-01-16
hi guys. newbie question. 

i have ubuntu installed on laptop and i want to remote to my windows desktop on LAN. 

is there any built in tool come out of box with ubuntu already / we need  a 3rd party software? 

brief google search told me to use samba ? . any suggestion ? 

what are the things i have to enable on both ubuntu and windows  so i can "control" my windows desktop ? thanks thanks

---

### Post by veloce on 2009-01-22
> **limanoit said:**
> hi guys. newbie question. 

i have ubuntu installed on laptop and i want to remote to my windows desktop on LAN. 

is there any built in tool come out of box with ubuntu already / we need  a 3rd party software? 

brief google search told me to use samba ? . any suggestion ? 

what are the things i have to enable on both ubuntu and windows  so i can "control" my windows desktop ? thanks thanks

You can use the rdp protocol with gnome-rdp not sure if it's installed by default but you can "sudo apt-get install gnome-rdp" if not.

I think Terminal Server Client is installed by default but it's not quite as easy to use.

Make sure you have remote desktop turned on on your windows box (it's in the system control panel item).

---

### Post by svrkispm on 2009-01-22
or try VNC.

---

