---
title: "Screen Resolution -not the usual"
date: 2007-08-07
forum: Desktop Environments
---

### Post by DaGGer on 2007-08-07
This isn't the normal I can't find the resolution I'm looking for. I searched and found that.  Now the problem I'm having is that I can't get the whole monitor to fill from side to side and up to top. now if this was a desktop monitor I could fix this with the controls on the monitor itself.  But this is on my fathers laptop. its an old dell and it could use a new OS (Windows was loaded with so much **** it wasn't funny) and seeing as how its so old and isn't that powerful it could use not running tons of graphical and back ground processes.  Now what I need to do it fill the screen up. If you need a picture of what I'm talking about tell me I'll get you one.

---

### Post by reckless2k2 on 2007-08-07
did you install the nvidia drivers from the restricted drivers area?

edit: sorry......i saw your specs. give the specs of your father's laptop. you may have to just edit the xorg.conf by hand. it's simple.

---

### Post by fistfullofroses on 2007-08-07
gedit /etc/X11/xorg.conf

then comment out the VertRefresh and HorizSync values.
scroll down and look for a driver listing under the device section.
Change that value to vesa.

---

### Post by RedSquirrel on 2007-08-08
Make sure you're using the appropriate video driver.

Here's a Howto for resolution that you may have already seen but I'll mention it just in case. It is possible that you might have to use a Modeline.

HOWTO: change resolution/refresh rate in Xorg
[http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)


If the laptop is really old (or you just want a really lightweight, responsive system), I recommed a minimal install with a light window manager such as Fluxbox or IceWM. Check out these links:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)


PS - If you edit /etc/X11/xorg.conf with gedit (or any graphical editor) you'll need to use **gksudo**:

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by DaGGer on 2007-08-09
Welll I tried to install the drivers but its a rather old system and I think it just uses defualt drivers. I really don't know.Its probably like 300-44 MHZ processor. that type of old.

---

