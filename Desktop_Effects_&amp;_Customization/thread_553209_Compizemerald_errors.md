---
title: "Compiz/emerald errors?"
date: 2007-09-17
forum: Desktop Effects &amp; Customization
---

### Post by shorty28898 on 2007-09-17
When i do compiz --replace and emerald --replace..  this comes up.

lindo@ubuntu:~$ emerald --replace

(emerald:6383): Wnck-WARNING **: Unhandled action type (nil)

(emerald:6383): Wnck-WARNING **: Unhandled action type (nil)

(those 2 lines are repeated about 50 more times...


and this..

lindo@ubuntu:~$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: not present. 
Checking for Xgl: not present. 
libGL error: drmMap of framebuffer failed (Invalid argument)
libGL error: reverting to (slow) indirect rendering

(gtk-window-decorator:6363): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6363): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6363): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6363): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6363): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6363): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6363): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6363): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6363): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6363): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

(gtk-window-decorator:6363): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6363): Wnck-WARNING **: Unhandled action type (nil)



and after a while (like ten minutes after starting compiz and emerald) the window bars go away..  like i cant maxamize minimize, or close anything... and once the borders go away, alt f2 does not work
i can type "emerald --replace" to get it all back, but once i exit the terminal that i typed it in, it all messes up

---

### Post by Forlong on 2007-09-17
First of all: the Wnck warning is nothing to worry about. Everybody has this in Feisty. It's finally fixed in Gutsy.

Then please tell us how you've installed Compiz Fusion and what type of graphics card are you using, there seems to be a problem with your 3D acceleration.

---

### Post by shorty28898 on 2007-09-18
Coincidently, this one:
[http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)

and its an intel graphics card

---

### Post by Nythain on 2007-09-18
you need some &'s in there if you are running from terminal
try
```

compiz --replace &

```and 
```

emerald --replace &

```
that should hopefully keep emerald running once you close the terminal... once you get your problems figured out it would probably be best to run compiz / emerald from a script or alt+f2 though, then you dont have to worry about closing any terminals at all :)

---

### Post by Forlong on 2007-09-18
> **shorty28898 said:**
>  its an intel graphics card
Then check if this will help you out: [http://wiki.compiz-fusion.org/Intel_with_AiGLX](http://wiki.compiz-fusion.org/Intel_with_AiGLX)

---

### Post by shorty28898 on 2007-09-18
perfect.  thank you both.

---

