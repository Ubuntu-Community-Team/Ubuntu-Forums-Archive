---
title: "Broken Gnome - unable to login to desktop please help!"
date: 2005-12-08
forum: General Help
---

### Post by zi99y on 2005-12-08
Okay I've been running ubuntu for a few weeks and was just getting confident and trying to iron out the remaining problems on my Acer 1694wlmi laptop, and have somehow broken it badly.

I've been having strange random wifi networking problems where I get disconnected sometimes, so I found [this thread]("http://www.ubuntuforums.org/showthread.php?t=97625") which sounded like the same problem. I proceeded to [install network manager as detailed here]("http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html#netmanager") and I added nm-applet to my session startup (priority 10) as advised, rebooted and now when I login to the Gnome gui, I just get the brown screen with the mouse, and a little disk activity, but my desktop never loads!

It may be useful to note that the brown theme isn't the one I use, I have blue backdrop, so it isn't getting far enough to load my settings even.

Another thing, is that I have 2 user accounts setup, and I have tried logging into the other one, which usually works and have the same result = crash.

The extra problem on top of this, is that using ctrl-alt-f1 or ctrl-alt-bkspace doesn't work, they just quit the gui and crash the system on a black screen leaving me to force a power down. I'm concerned that I have damaged some files in doing this as it's happened quite a lot.

I can gain access to the system only by booting the grub recovery mode to a root shell, but I'm not sure what I can do. 

Please help me, I've had to load windows......

---

### Post by blueplazma on 2005-12-08
It sounds like your problem may be that your loopback interface is not coming up.  Without that, X is unable to load and it will crash.  Try bringing X up in the failsafe configuration and see if that works.  If not, try going into single-user mode and looking in your log files.  Make sure your firewall (if you have one) is set to allow all connections to/from the loopback to/from the loopback.

---

### Post by zi99y on 2005-12-08
you sir, are a genious! I thank you so very much.

Turns out I did something a little silly, reading that T42 article today I read the part that mentions disabling auto loading the interfaces in the interfaces file, and stupidly didn't check before I commented out the IO line....

A little knowledge is a dangerous thing, ..... But I'm learning :D

thanks again

---

