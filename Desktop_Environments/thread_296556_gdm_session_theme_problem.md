---
title: "gdm session theme problem"
date: 2006-11-09
forum: Desktop Environments
---

### Post by Crypto-138 on 2006-11-09
For some reason, ever since I updated to Edgy Eft,
I can't change the gnome themes in any other session but my GNOME session.

I have XGL/Beryl installed as a "Xgl" session under gdm, and for some reason,  the controls and icons are all the default ones and I can't change them. Here's a screenshot (If I can get images to work; the avatars sure don't)

[IMG]http://img361.imageshack.us/img361/6707/screenshotzt8.png[/IMG]

Strangely, metacity still works.

[[Sorry for the large picture, I'll get a thumbnail if ya want]]

---

### Post by Crypto-138 on 2006-11-10
I figured it out. /usr/bin/local/startxgl.sh should read:

> 
#!/bin/sh
Xgl :1 -fullscreen -ac -br -accel xv:fbo -accel glx:pbuffer &
sleep 4  
export DISPLAY=:1
**exec dbus-launch --exit-with-session gnome-session**


My last line was 
> exec /usr/bin/gnome-session

---

### Post by Crypto-138 on 2006-11-11
Solved.

---

