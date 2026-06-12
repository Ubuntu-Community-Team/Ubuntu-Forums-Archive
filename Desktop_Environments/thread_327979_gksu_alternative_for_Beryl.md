---
title: "gksu alternative for Beryl"
date: 2006-12-30
forum: Desktop Environments
---

### Post by inzpektor on 2006-12-30
Hey folks.

I am running Beryl on Edgy and it's great fun.  However, when I f.ex. wanna open synaptic, and the gksu app appears, it completely - pardon my french - screws up beryl; window-borders on new windows disappear often times or the windows are missing the window-state buttons (actually, they are there, they are just invisible).  My desktop then slows down, and what should have been a cool desktop suddenly becomes a carpet of crap.

So, as I suspect the screen-dimming feature of gksu to be causing this havoc, is there a way to either configure gksu not to dim the screen or completely substitute gksu with something else? - I remember an app called gnome-sudo (in Hoary, I believe) which did not dim the screen, but it's gone from the repositories, apparently.

Tanks

---

### Post by d3v1ant_0n3 on 2006-12-30
What version of Beryl are you running, and on what hardware? 

I have seen a similar problem with Beryl (basically, gksu can be a bit...ugly for me sometimes), but not seen it take out window decs for a while.

---

### Post by inzpektor on 2006-12-30
Hi d3v1ant_0n3.

Thanks for the quick reply.  I'm running Beryl v.0.1.4 (synaptic says 0.1.4~0beryl1) on a Thinkpad T41 with an ATI Radeon Mobility M7 LW (Radeon 7500) GPU.  I've not installed the radeon-drivers from freedesktop.org since I read that Edgy's got those drivers included in the xserver-xorg-video-ati package, which is already installed.  (fglrx does not support this GPU)

Dunno if it's important, but glxinfo says: (amongst other things)
```
libGL warning: 3D driver claims to not support visual 0x4b
Disabling HW TCL support
```

The TCL-thing is my own work, cause I get much better performance that way.

---

### Post by moma on 2006-12-30
Try this.
Start gconf-editor (as normal user)
$ [COLOR="SeaGreen"]gconf-editor[/COLOR]

And browse to /apps/gksu.  Then mark the "disable-grab" option. It disables the annoying and flashing dimming.  See the picture.
[[img]http://bildr.no/thumb/28285.jpeg[/img]](http://bildr.no/view/28285)

---

### Post by bihe on 2006-12-30
nice one - thanks

---

### Post by inzpektor on 2006-12-30
Thanks, man.  That did the trick.  Now, gksu looks just like the gnome-sudo app and everything works as it should with beryl running.

---

