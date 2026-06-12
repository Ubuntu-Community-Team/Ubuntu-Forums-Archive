---
title: "gksu error"
date: 2006-05-18
forum: Desktop Environments
---

### Post by vaskark on 2006-05-18
I'm encountering this error when using gksu:
```
$ gksu synaptic
Xlib: No protocol specified

(synaptic:16529): Gtk-WARNING **: cannot open display:

``` Any ideas?

---

### Post by infoburner on 2006-05-18
try gksudo maybe?

---

### Post by girts on 2006-05-18
The same problem here
gksu and gksudo gives this:
> Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(users-admin:11167): Gtk-WARNING **: cannot open display:


so users-admin, synaptic and other items from administration menu that require password can't be run. However, *sudo synaptic * from terminal works fine.

---

### Post by vaskark on 2006-05-18
Yeah I should have stated that gksudo isn't working for me either.

---

### Post by N0thing on 2006-05-21
Im encountering this same error and if i turn firestarter off it doesnt occur. Sometimes if i enable the ToS (type of service) option it works. Its on and off and its becoming a pain.

---

### Post by denkedran on 2006-05-24
```
gksu synaptic
sh: /usr/X11R6/bin/xauth: Datei oder Verzeichnis nicht gefunden
sh: /usr/X11R6/bin/xauth: Datei oder Verzeichnis nicht gefunden
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(synaptic:6955): Gtk-WARNING **: cannot open display:
```

this was my error. synaptic from menu didn't work either.
doing the following
```
sudo ln -s /usr/bin/xauth /usr/X11R6/bin/xauth
```
helped me to solve the problem

---

### Post by audie on 2006-05-31
Has anyone resolved this ? I'm having the same issue.

---

### Post by btlee on 2006-05-31
[QUOTE=audie]Has anyone resolved this ? I'm having the same issue.[/QUOTE]

I have no problem, but would you try this?

xhost +localhost
gksu synaptic

---

### Post by %hMa@?b&lt;C on 2006-06-01
running this should fix it 
```
xhost +local:
```
-jeff

---

