---
title: "Dark Oberon and libfmod-3.75.so"
date: 2007-01-03
forum: Gaming &amp; Leisure
---

### Post by cripou on 2007-01-03
Hi,

i just installed Dark Oberon from its deb file. it installed all right and i now have the icon in my menu. only problem is: when i click on it nothing happens... so i tried through the terminal to see what the problem was and it gave me this: 
```
cripou@cripoubuntu:~$ dark-oberon
dark-oberon: error while loading shared libraries: libfmod-3.75.so: cannot open shared object file: No such file or directory
```

anyone knows what i could do to make it work...

---

### Post by diepruis on 2007-01-03
You need to install the libfmod package. Unfortunately, this isn't in the repositories, so you'll need to go find it on the internet.

---

### Post by cripou on 2007-01-03
all right! I found that:
```
wget http://www.fmod.org/files/fmodapi375linux.tar.gz
tar -zxvf fmodapi375linux.tar.gz
cd fmodapi375linux/api
sudo cp libfmod-3.75.so /usr/lib/
cd ../..
rm fmodapi375linux.tar.gz
rm -Rf fmodapi375linux
```
which seemed to have worked...

but now this is what i get:
```
cripou@cripoubuntu:~$ dark-oberon
Info: Loading configuration from '/home/cripou/.dark-oberon/config.cfg'
Crit: Can not open OpenGL window

```

any idea what i can do next...?

---

### Post by diepruis on 2007-01-03
All I can think of is your video drivers. Are they correctly installed? If you don't know, then post the output of ```
glxinfo
``` Or better yet, put it into an attachment. Also, please post what type of graphics card you have.

---

### Post by cripou on 2007-01-03
output of "glxinfo"
```
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x3b 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

graphic card:
ATI Mobility Radeon 7500

---

### Post by diepruis on 2007-01-04
Looks like your graphics card isn't set up correctly. Have you installed the fglrx drivers? Please try following [this](http://ubuntuforums.org/showthread.php?t=204910) guide, if you haven't.

---

### Post by atomkarinca on 2008-05-20
For people that encounter this error here's the workaround:

```
wget http://www.fmod.org/index.php/release/version/fmodapi375linux.tar.gz
tar -xvzf fmodapi375linux.tar.gz
cd fmodapi375linux/api
sudo cp libfmod-3.75.so /usr/lib
```

and you're good to go.

---

