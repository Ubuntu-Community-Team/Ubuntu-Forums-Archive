---
title: "How do I speed up Remote Desktop (VNC)?"
date: 2006-08-20
forum: Desktop Environments
---

### Post by Kethinov on 2006-08-20
I use GNOME's remote desktop feature to connect to my computer from elsewhere, but with capped (50kps) upload on the server I've found it to be an exercise in masochism. What can I do to speed up the VNC session? Can I reduce the quality of the picture the server sends or something?

---

### Post by scxtt on 2006-08-20
you're using vino to share your :0 session ... i recommend using **vncserver** so you can specify depth as well as other options ...

---

### Post by Kethinov on 2006-08-20
How do I replace vino with vncserver?

---

### Post by scxtt on 2006-08-20
**sudo aptitude install vncserver** is what i use ... some people talk about **tightvncserver** (and the like) but i've never had any reason to use it ...

and this is my alias to start a vnc server:
[indent]alias vncserver='vncserver -geometry 1600x1200 -depth 24'[/indent]you can bump down the **-depth** flag to save you some data transfer and/or use a lower depth setting on the viewer ... i'm not entirely sure which will be better since i always use 24bit and "full color" ...

---

