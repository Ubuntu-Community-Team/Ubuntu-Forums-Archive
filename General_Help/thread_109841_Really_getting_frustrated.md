---
title: "Really getting frustrated"
date: 2005-12-29
forum: General Help
---

### Post by Old *ix Geek on 2005-12-29
I'm having a multitude of problems, some of which I've posted about (but never gotten solutions for), and I'm really getting exasperated.  Let me point out that I started using UNIX in the mid-1980s, and was accustomed to NEVER having anything crash, NEVER being unable to get things to work (even if it took some tweaking/troubleshooting), etc.  Now, obviously, I realize that today's computers and software are much more complex than they were back then, but as a longtime proponent of Linux/UNIX--and as vehemently anti-Micro$oft as possible--I expect to be able to tell people--truthfully--about how great Ubuntu is.  But I'm having so many problems, it's impossible to do that.  I should also point out that there have been gaps in my use of *nix over the years, when work and other factors drove me to the dark side.  :(   So I'm not as up on things as I used to be.  For example, I used to be able to troubleshoot just about anything--peripherals not working, programs running amok, kernel issues, etc., but now I feel a bit lost at times.  So I'd appreciate some help.

One issue is the GIMP crashing.  Sometimes it's absolutely random, while I can reproduce with 100% success other things that will cause it to crash.  I really need to be able to use the GIMP, but it's basically impossible.  I just spent 20 minutes creating, fine-tuning, and adjusting a graphic until it was perfect...then I went to 'save' it and, POOF!, the GIMP shut itself down.  FWIW, I'm using 2.2.

Another problem is my digital camera, a Kodak EasyShare DX3900.  I have been absolutely unable to get Ubuntu to even recognize its existence.  However, other devices plugged into the same USB ports are recognized, so it's not a port problem.

Then there are audio CDs.  They play...but without sound.  I mean you can watch the CD player software cranking away as it proceeds through the tracks, but there's no sound.  I have NO other sound problems except for audio CDs, so it's not a sound card issue, etc.

There are other problems, but I guess that's enough for now!  Also, I must say that it's definitely NOT all bad.  For example, I've figured out how to configure/use things that didn't even exist back in the old days, like wine and samba, and printing to a 'doze printer, and other stuff like that.  So I'm making a lot of progress, but I just want to get these kinks worked out.

---

### Post by quonsar on 2005-12-29
about cd player sound - i'm not being a wise guy here, i made this mistake myself - but are you sure the volume is on? there is a volume control on the cd player which was all the way off when i ran it! really had me going for a while! 

also, bring up the mixer by typing in a terminal:

```
gnome-volume-control
```

and be sure the CD player control is up and not muted. also check the same on alsamixer:

```
alsamixer
```

some of these settings are muted by default for some reason!

---

### Post by kleeman on 2005-12-29
Your camera is supported by libgphoto:

[http://gphoto.sourceforge.net/proj/libgphoto2/support.php](http://gphoto.sourceforge.net/proj/libgphoto2/support.php)

When you plug it in try executing these commands with a cli:

dmesg

lsusb

The first will show whether the kernel has seen the camera and the second should list it as a usb port.

I might be able to help with audio later.

---

### Post by kleeman on 2005-12-29
You might also want to look at this:

 [http://howtos.linux.com/howtos/USB-Digital-Camera-HOWTO/index.shtml](http://howtos.linux.com/howtos/USB-Digital-Camera-HOWTO/index.shtml)

---

### Post by Old *ix Geek on 2006-02-09
Well, an unexpected surgery and its recuperation have kept me from getting back to this...but I'm back now!

Of the issues I originally addressed, I still haven't resolved the camera or the 'silent CD' problems.  The camera is most important to me right now, so I'd appreciate help with it.

I have followed the advice above but still cannot get Ubuntu to recognize that there's a camera plugged in.  And, just to reiterate, it DOES recognize other USB devices plugged into the same port(s).  I've also followed the advice/procedures I've found elsewhere around the 'net, but it's still not working.

---

### Post by kleeman on 2006-02-10
You need to be a bit more interactive here if you want answers :) :) 

What are the outputs of
dmesg
lsusb

before and after you plug in the camera?

---

