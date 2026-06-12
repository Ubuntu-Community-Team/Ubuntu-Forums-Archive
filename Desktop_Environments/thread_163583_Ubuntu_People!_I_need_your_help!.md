---
title: "Ubuntu People! I need your help!"
date: 2006-04-21
forum: Desktop Environments
---

### Post by Muhammad on 2006-04-21
Why hello there,

First of all, what the hell happened to the forum?

Second, can anyone tell me where I could find a guide/howto/faq on how to install ubuntu server with Fluxbox only (No Gnome or KDE)? Your assistence is greatly appreciated. :)

---

### Post by ESPOiG on 2006-04-21
here is a link to install Fluxbox... but it shoudnt be to hard to install it via just an install of server

[http://www.ubuntuforums.org/showthread.php?t=116759](http://www.ubuntuforums.org/showthread.php?t=116759)

try using your repositories as dapper instead of breezy if this is the way you are going, and then you dont have to compile the latest version

hope this helps, ESPOiG

---

### Post by Muhammad on 2006-04-21
Thanks for the reply, but this is not what I'm looking for... I need a guide just like the one about Xubuntu that existed back when Hoary was the stable version.

---

### Post by ESPOiG on 2006-04-21
yeh but i dont see how it could be that hard... that tutorial just explains howto install it with gnome or kde... just install ubuntu as server then install Fluxbox from the repositories as you would Xfce, i think it could work i dont see why not :D... anyway it was worth a shot

---

### Post by Muhammad on 2006-04-21
But I only have 900mbs of free space, plus I haven't used Ubuntu in a long time, so I'm back to Zero here. :(

---

### Post by codejunkie on 2006-04-21
[QUOTE=Muhammad]But I only have 900mbs of free space, plus I haven't used Ubuntu in a long time, so I'm back to Zero here. :([/QUOTE]
do a server install then run ```
sudo nano /etc/apt/sources.list
```uncomment the universe line save the file with ctrl+x then run ```
sudo apt-get update
``` then 
```
sudo apt-get install fluxbox fbdesk fbpager fluxconf xterm xserver-xorg gdm
```
this should do it.

---

### Post by Muhammad on 2006-04-21
Thanks a bunch!

---

### Post by Muhammad on 2006-04-21
Alright, I did exactly what you told me, and I'm getting an error cannot start Xserver, so basically the Xserver is crashing whenever it's trying to start... What should I do now?

---

### Post by art on 2006-04-21
What are the error messages? you probably are missing Video card drivers, since you did a server install. I am just guessing here... What graphics card do you have?

---

### Post by Muhammad on 2006-04-21
An Intel 82815 Graphic Controller, it's not a Geforce, it's old, but it does it's job on Windows at least...

---

### Post by art on 2006-04-21
Try installing xserver-xorg-driver-i810

---

### Post by Muhammad on 2006-04-21
Will do, be back in a sec...

---

### Post by Muhammad on 2006-04-21
Tried it, no dice...

I also tried installing linux-686, no luck either...

---

### Post by art on 2006-04-21
What is in the /var/log/Xorg.0.log? The errors must be listed there...

---

### Post by Muhammad on 2006-04-21
I went there, and I found a damn huge list of errors. I scrolled down a bit, appearantly I needed to install Xfont-base. So I did, and now I'm running Fluxubuntu! Many thanks.

---

