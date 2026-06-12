---
title: "XGL produces graphical garbage"
date: 2007-09-18
forum: Desktop Effects &amp; Customization
---

### Post by wiberg on 2007-09-18
Hi, i have a problem with installing XGL. When I start an XGL session it looks like this (see attachment).
Note that the clock seems to be unaffected :/
The memory on my graphics card is alright, i have no trouble whatsoever running a regular x.org session.
I have an ATI x1300 card running with fglrx on Ubuntu 7.04.
My goal is to get Compiz running.
Maybe I have to tweak some config file or something?

wiberg

---

### Post by Jouke74 on 2007-09-18
The latest FGLRX driver does that yes. I don't know whether there is a solve for it already, but there are a few more threads about it.

---

### Post by NovaAesa on 2007-09-18
I'm having this exact same problem. My screen input is very similar after starting a session with GNOME and XGL. I am also trying to get Compiz Fusion happening!

---

### Post by wiberg on 2007-09-18
Jouke74,
>The latest FGLRX driver does that yes.
Thus downgrading fglrx should work, shouldn't it?

---

### Post by Forlong on 2007-09-18
Just use the fglrx driver from Ubuntu's repositories. It works well with Xgl.

---

### Post by Jouke74 on 2007-09-18
Indeed, downgrading should work. The FGLRX from Ubuntu (restricted) works well for me, but is slower.

---

### Post by Mavtech on 2007-09-18
Which directions did you use for installing Compiz?  Check your startxgl.sh.  This happened to me initially when I used some install directions that left out a dash in this file.  This is with the latest ATI drivers from Envy.

Open the file in the editor:

```
sudo gedit /usr/local/bin/startxgl.sh
```

Make sure there are 2 dashes in "--exit-with-session".

```
#!/bin/sh
Xgl :1 -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```

---

### Post by cyclocross on 2007-09-18
I've also got some graphical garbage.  Seems after an update for compiz got pushed down my black and white have reversed.  I followed [http://ubuntuforums.org/showthread.php?t=488385&highlight=compiz-fustion](http://ubuntuforums.org/showthread.php?t=488385&highlight=compiz-fustion)
compiz version is 1:0.5.2-Oubuntu3~ppa4(feisty)
I'm using xorg-driver-fglrx, the 7.10-8.34.8+2.6.20.5-16.29(feisty-security)
except I have switched to the amaranth repository thinking this might solve the problem, but it didn't. Any ideas on what may be causing this?  And how to fix it?

---

### Post by wiberg on 2007-09-19
i followed [https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl) for installing xgl. it recommends ending the current x.org session and start an xgl session. i, however, recommend a complete reboot, because now it works

---

### Post by jcrow on 2007-09-22
I have a similar problem. When I use the latest kernel, the display is messed up and I have no sound. I have just been using the earlier kernel that Fiesty came with and everything is ok. We'll have to see what Gusty brings.

---

### Post by chalewa on 2007-09-25
> **jcrow said:**
> I have a similar problem. When I use the latest kernel, the display is messed up and I have no sound. I have just been using the earlier kernel that Fiesty came with and everything is ok. We'll have to see what Gusty brings.

same thing happened to me after i upgraded to the latest kernel...this is now the second kernel update that has rendered my machine useless.

---

