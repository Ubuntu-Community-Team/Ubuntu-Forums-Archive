---
title: "XGL + Compiz @ Xubuntu - Some questions"
date: 2006-09-19
forum: Desktop Environments
---

### Post by KlausPaiva on 2006-09-19
Hello people!

I've sucessfully installed XGL + Compiz on my Xubuntu box. Everything is working smooth and well. But, there are some things I still don't know how to do:

* Xubuntu has a default keyboard shortcut for "Run" command: Alt + F2, but when I'm using XGL it's no longer works. (my question here is: where I assign keyboard shortcuts on XGL?)
* By using csm, all the changes I make doesn't apply.

Basically, I which to know where Compiz stores it's configuration files so then I could change then manually. (I have in my home a file: .compiz/csm_settings, but it doesn't seem to be read...)

Thanks!

---

### Post by distroman on 2006-09-19
Check your xorg.conf to see if your keyboard layout is setup right. 

If you are really having trouble with .compiz/csm_settings you might need to set the right permissions. 

Hope I pointed you in the right direction.

---

### Post by davea402 on 2006-09-19
hi guyz,

i have tried basically everything to make my xgl work again...but it won't.  it was working untill i did the update after 2 months, now it doesn't work.

-life:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 2.0.5814 (8.25.18)

my fglrxinfo output and i have also changed the /etc/X11/xorg.conf to fglrx....i think it has something to do with compiz.  when i log into the xgl section nothing is responsive.  the windows do not have min,max,close buttons on the top and the xgl basically does not work...no cube no nothing....if needed more info let me know...

---

### Post by MetalMusicAddict on 2006-09-19
Compiz takes over as your window manager so its in control of your keyboard shortcuts. Same thing happens in Gnome. You have to setup the keys in the Compiz config app.

---

### Post by davea402 on 2006-09-19
what about the whole xgl not working....the cube is not set up or anything...when i first started with compiz it was good, it set up the shortcuts for me...but after the update....nothing is responsive....but another question i have is how come the window borders are gone...min,max,close are not there anymore...

---

### Post by KlausPaiva on 2006-09-20
Great news!

I was using a shell script like this to start XGL / Compiz:

```
#!/bin/bash
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer &
#The option '-fp /usr/share/fonts/X11/misc/' is not appropriate in my set-up
#Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer -fp /usr/share/fonts/X11/misc/ &
sleep 1
DISPLAY=:1 LD_LIBRARY_PATH=/usr/lib/opengl/xorg-x11/lib compiz --replace decoration fade minimize bs cube resize dbus move neg place rotate state switcher trailfocus water zoom showdesktop & sleep 1
DISPLAY=:1 xmodmap -e "keycode 22 = BackSpace" &
DISPLAY=:1 cgwd --replace &
#DISPLAY=:1 xterm & #not strictly required but handy
DISPLAY=:1 xfce4-session
```

By changing the first "DISPLAY" line as follows:

```
DISPLAY=:1 LD_LIBRARY_PATH=/usr/lib/opengl/xorg-x11/lib compiz --replace dbus csm decoration fade minimize bs cube resize move neg place rotate state switcher trailfocus water zoom showdesktop & sleep 1
```

Everything worked fine! Now I have XGL running really fast (by reading my Compiz settings) and with all the keyboard shortcuts I wanted too.

Thanks guys!

---

### Post by blakesmith on 2006-09-20
I get a 800x600(desktop) on a 1280x1024 resolution on the top left of my screen and cannot seem to find a way to fix this, any ideas?

---

### Post by davea402 on 2006-09-21
hey sorry i tried the your script and xgl won't even start...grrr

> **KlausPaiva said:**
> Great news!

I was using a shell script like this to start XGL / Compiz:

```
#!/bin/bash
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer &
#The option '-fp /usr/share/fonts/X11/misc/' is not appropriate in my set-up
#Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer -fp /usr/share/fonts/X11/misc/ &
sleep 1
DISPLAY=:1 LD_LIBRARY_PATH=/usr/lib/opengl/xorg-x11/lib compiz --replace decoration fade minimize bs cube resize dbus move neg place rotate state switcher trailfocus water zoom showdesktop & sleep 1
DISPLAY=:1 xmodmap -e "keycode 22 = BackSpace" &
DISPLAY=:1 cgwd --replace &
#DISPLAY=:1 xterm & #not strictly required but handy
DISPLAY=:1 xfce4-session
```

By changing the first "DISPLAY" line as follows:

```
DISPLAY=:1 LD_LIBRARY_PATH=/usr/lib/opengl/xorg-x11/lib compiz --replace dbus csm decoration fade minimize bs cube resize move neg place rotate state switcher trailfocus water zoom showdesktop & sleep 1
```

Everything worked fine! Now I have XGL running really fast (by reading my Compiz settings) and with all the keyboard shortcuts I wanted too.

Thanks guys!

---

