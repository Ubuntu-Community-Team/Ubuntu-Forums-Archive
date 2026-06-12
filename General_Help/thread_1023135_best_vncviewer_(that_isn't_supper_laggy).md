---
title: "best vncviewer (that isn't supper laggy)"
date: 2008-12-27
forum: General Help
---

### Post by mishkin on 2008-12-27
on windows vista I use real vnc viewer and get <300ms lag (it's noticible but i don't ussually even notice it)

on ubuntu eee I'm using the preinstalled remote desktop viewer and it's very laggy like 2000ms lag...

I'd like a client that has gui and remembers the last ip used

I'm running gnome and my server is running xfce4 (debian etch)

---

### Post by jimmy the saint on 2008-12-27
I use gnomeRDP (its in add/remove) to interface with my iphone.  It seems to work better than the default app.

---

### Post by my_key on 2008-12-27
I get real good results with TightVNC, even over ssh, but I do have a reasonably fast connection. However, I find that I can achieve super fast speeds by using freeNX (different protocol than VNC, but it achieves the same result as vnc, namely viewing your other desktop).

I do recomment changing the desktop environment that vnc logs into to something lightweight as fluxbox. I find this makes my vnc connections much much faster.

---

### Post by jrusso2 on 2008-12-27
There are some settings that decrease lag in VNC like running a lower resolution, and running less colors.

---

### Post by ugm6hr on 2008-12-27
tsclient

I think it is essentially a GUI to vncviewer (amongst other things).

```
sudo apt-get install xtightvncviewer tsclient
```

It appears in Applications->Internet->Terminal Server Client

You can save "profiles" for future single click connections.

---

### Post by mishkin on 2008-12-27
thanks  for the replys but I solved it myself, terminal server client in "internet" (eee unbunu) worked after I installed some library files from 2001 lol (it was giving an error)

it appears to be next to lagless (I have 2 dsl combined 10mbit)

so default app ftw :O

(I'd gone off googleing after I posted this is how I solved it)

---

