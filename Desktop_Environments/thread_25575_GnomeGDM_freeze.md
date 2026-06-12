---
title: "Gnome/GDM freeze"
date: 2005-04-10
forum: Desktop Environments
---

### Post by crim on 2005-04-10
Hi Everybody,

I did a fresh installation of Hoary, everything went well booted straight to the gdm greeter. Then things went wrong. If I click on anything, like languages or sessions I get a white box and a total lockup of gdm. The system is unresponsive locally but I can still ssh into the box, check out the logs etc. Nothing strange in the logs that I can see.  If I just try and do a straight login to gnome I get a blank brown background with mouse movement but no keyboard interaction and gnome doesn't load.  Has anyone else experienced this? 

Its a dual athlon mp box/ gig of ram / scsi hard disk, some generic sb16 sound card.

Any ideas? Thanks.

---

### Post by odix on 2005-04-13
same symptoms for me, using nv drivers in xorg.

Hardware: AthlonXP /GeForce FX6xxx

---

### Post by Oam on 2005-04-13
[QUOTE=odix]same symptoms for me, using nv drivers in xorg.

Hardware: AthlonXP /GeForce FX6xxx[/QUOTE]
 - Boot recovery move
- edit the /etc/X11/xorg.conf
- find the Device section for display adapater 
- change the driver from "nv" to "nvidia".

Worked for me! :)

---

### Post by Trevor Bramble on 2005-04-13
[QUOTE=Oam]- Boot recovery move
- edit the /etc/X11/xorg.conf
- find the Device section for display adapater 
- change the driver from "nv" to "nvidia".

Worked for me! :)[/QUOTE]

I'm unfamiliar with Nvidia, but I suspect this is the same as changing out "fglrx" for the "ati" driver as that's how I avoid the freezing problem as well.

Unfortunately that's entirely contrary to my goal of using 3d acceleration.

---

### Post by kamstrup on 2005-04-13
Can you log into failsafe mode?

---

### Post by Trevor Bramble on 2005-04-13
Speaking for myself and not the original poster, It's not a problem with booting up.  

When fglrx is called from xorg.conf: If I boot all the way to GDM it will present me with a picture perfect GDM login screen and, depending, I can sometimes bring up a very corrupt Sessions menu without freezing.  If I attempt to login, I can still move the mouse pointer around until I get bored/despondent/enraged as the login window becomes a static image and no GUI loads.  Alt+Ctrl+F*n*, like any other keyboard input at that point, is completely ignored.

Upon reboot I can move to a tty, stop GDM, swap out the xorg.conf file with one that uses the "ati" driver, and reboot into a perfectly fine desktop that has no 3d acceleration except the pitiful Mesa3D.  Incidentally, I can't just reload GDM after swapping out the driver because the resulting display is about 90% corrupted (I can see the pointer move behind a lot of noisy vertical bars).

---

### Post by odix on 2005-04-17
[QUOTE=Oam]- Boot recovery move
- edit the /etc/X11/xorg.conf
- find the Device section for display adapater 
- change the driver from "nv" to "nvidia".

Worked for me! :)[/QUOTE]

thanks, worked for me too

odiX

---

### Post by OzPhoenix on 2005-04-24
Hi Everyone,

I think I'm having the same (or a very related) problem. After boot up, I get a perfect login screen and can happily login. Then I get to the desktop and everything is still perfect. I can run various apps and terminals and be happy for an extended time - sometimes more than 24 hours.

But then it seems if I minimize a window suddenly everthing freezes. I still can move my mouse, but I can't send any key strokes. Further I still get (sorry for not knowing the names) the bar at the top (with Applications, Places and System) and the bar at the bottom showing the current windows. But I can not click on either of these bars. And between these bars (where the desktop would normally be) is all white.

So I think it's the same, but just interesting that I get some degree of stability for a random extended period of time. I'm running an AMD Athlon XP2000+ with 512 MB RAM and an Nvidia GeForce FX6600.

I saw the suggestion to change the Display Adapter from "nv" to "nvidia" and I plan to try that. But could someone please tell me what the difference is, and why this would help?

Cheers.

---

### Post by OzPhoenix on 2005-04-24
I tried changing it from "nv" to "nvidia" but then after restart GDM / X failed to start. So I had to put it back. Do I need to install something to be able to use "nvidia"?

---

### Post by diego on 2005-05-02
:-? I have the same problem and I do use NVIDIA in my xorg.conf. :(
I installed nvidia-kernel-src and compiled it (make-kpkg) for my machine (amd64), maybe that was it ...
How did you guys do it?

Please, help!!

---

### Post by OzPhoenix on 2005-05-02
Hi Diego,

I got mine working in the end quite happily. I went into synaptic (the pkg manager thingy) and added the package **nvidia-glx**. Once that was installed I ran the command that is in the description for nvidia-glx. (Sorry I can't tell you the cmd, I'm not on an ubuntu box at the moment.)

Now that that is all done, it works like a charm. But I also tried changing nv to nvidia, but that did not work. It was only when I did the above that everything became beautiful.  :smile:

Best Wishes,
OzPhoenix.

---

