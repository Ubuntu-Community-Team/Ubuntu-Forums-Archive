---
title: "Help installing xserver"
date: 2008-04-26
forum: Debian
---

### Post by the_real_fourthdimension on 2008-04-26
I have an ancient laptop that I installed debian on this morning.  Since it has a tiny HD, I installed as little as possible during the install process and figured I could add the extras later on.  So I just now installed xserver via this command:
```
apt-get install xserver-xorg-core
```
Now that I think I finally found the correct graphics settings to use, it has font trouble and won't start up.  I get a lot of this:
```
Could not init font path element /user/<share or X11R6>/<fonts or lib>/X11/...and dpi's, etc. , removing from list!

Fatal server error:
could not open default font 'fixed'
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
after 0 requests (0 known processed) with 0 events remaining.
```

I read on a few other forums that I might not have a font server installed?
Does anyone know how to fix this?  
Thanks.

---

### Post by Unbound Spectre on 2008-04-27
Install xfonts-base.

---

### Post by the_real_fourthdimension on 2008-04-29
Thanks.  That worked, but now I get this error:
[CODE]
AIGLX screen 0 is not DRI capable
[CODE]

What should I do now?

---

### Post by Unbound Spectre on 2008-04-29
Take a look here. [http://www.linuxquestions.org/questions/debian-26/aiglx-screen-0-is-not-dri-capable-599336/](http://www.linuxquestions.org/questions/debian-26/aiglx-screen-0-is-not-dri-capable-599336/)

---

### Post by the_real_fourthdimension on 2008-04-29
Yeah, I checked out that thread before I posted here.  I tried every suggestion there, and each one had no effect, so I ended up undoing all the changes and posting here.
It puzzles me because it worked once, and then something changed because I rebooted and ever since I've gotten this error.

---

### Post by Unbound Spectre on 2008-04-29
You may need someone with more experience than I, try posting at the Debian forums. [http://forums.debian.net/](http://forums.debian.net/)

---

### Post by the_real_fourthdimension on 2008-04-29
OK.  Thanks for all your help :)

---

