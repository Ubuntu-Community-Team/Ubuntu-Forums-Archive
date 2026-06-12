---
title: "ATI Radeon (noob alert)"
date: 2006-01-09
forum: Desktop Environments
---

### Post by Snackmaster on 2006-01-09
Okay so I read a bunch of posts on ATI cards, fglrx etc.
I've manually update xorg.conf to support my monitors refresh rates (yah!)
this made me brave...
So I followed intructions from these forums on installing and switching to FGLRX drivers thinking that would help. Well... I'm getting better at installing Ubuntu :)
so...
With fresh install #2 I downloaded the Ubuntu ATI package, it installed fine including dependencies. I rebooted, nothing happened.

So say you, how does a guy get the proper basic nothing fancy ATI drivers installed and running for his ATI Radeon 9000 card? I certionaly don't have the Nvidia TNT card Device managers seems to indicate is configured!

I ask because (a) my video performance is very very very poor on a 768meg of Ram, 64meg video, 1,7ghz P4 and (b) because I'm baffled that Ubuntu can't detect my ATI card or my Dell P991 monitor during install both of which are very common and a good 3+ years old, especially since (c) I just installed an official Ubuntui ATI package titled "xserv-xorg-driver-ati" v 6.8.2.77 from Synaptic Package Manager so it appears support is there out of box.

Thanks,
snack

---

### Post by Imexius on 2006-01-10
try adding Option "noaccel" to your xorg.conf

---

### Post by Perfect Storm on 2006-01-10
[http://doc.gwos.org/index.php/Install_ATI_driver](http://doc.gwos.org/index.php/Install_ATI_driver)

---

### Post by Snackmaster on 2006-01-10
The method I followed in these forums closely follows the link above.

Serious serious issue with this method, it assumes (A) you've already installed the Ubuntu ATI drivers which don't work and more importantly installed the dependent packages that install with the Ubuntu ATI drivers that don't work. I'm going to assume that's how I ended up at the Black Screen of Death ;)

On my ATI card driven machine after two installs both times the ATI drivers were not installed and my card appears to have been detected as Nvidia (Device Manager says Nvidia TNT Pro).

So why doesn't the Ubuntui ATI package titled "xserv-xorg-driver-ati" 6.8.2.77 from Synaptic Package Manager work, or how can I get it to work?

or do I install that first and then FGLXR?

man o man if you're gonna have a GUI you gotta make it work...

---

