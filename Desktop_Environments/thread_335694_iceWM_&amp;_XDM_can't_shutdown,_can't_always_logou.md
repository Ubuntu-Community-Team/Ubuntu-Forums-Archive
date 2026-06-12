---
title: "iceWM &amp; XDM: can't shutdown, can't always logout"
date: 2007-01-10
forum: Desktop Environments
---

### Post by wafer on 2007-01-10
I've installed Ubuntu on an older laptop (VAIO PCG-N505VE - 333MHz Centrino, 64MB RAM).  To do this, I've used the [[COLOR="Blue"]Installation/LowMemorySystems[/COLOR]]("https://help.ubuntu.com/community/Installation/LowMemorySystems") How-to as a template for system installation.  I've installed XDM and iceWM as my login manager and window manager along with some other packages.  Everything seems to be working fine (I'm learning a heck of a lot).  The most important problem I have is that there is no Shutdown option.  Currently I'm just doing the CTRL-ALT-F1 (to exit XDM) and CTRL-ALT-DEL (to reboot) thing from the XDM login screen and trying to time the system shutdown to happen during system POST - which is problematic because it takes about 5 sec. holding the power button to shutdown the PC power, so timing is critical - I definitely don't want to mess up my HDD.  

Is there a script I can add to some configuration files that will add a working "Shutdown" item to the iceWM menu or a shutdown button to the XDM login screen?  I've scoured these forums and googled the heck out of this and only found passing reference to being able to do this, but no detailed instructions.  I'm a noob, so details are important.  

As a passing problem, sometimes logout does not work from iceWM.  Not sure why, it seems to happen after I've been logged in for a while and have used several applications.  If I log in and immediately log out, everything works fine.  My current work-around is to exit iceWM by switching to Xterm and type exit at the prompt.  This takes me to the XDM login screen.  Still can't shutdown though.

Any ideas?

wafer

---

### Post by kerry_s on 2007-01-10
Remove XDM and install GDM. XDM is a antic in linux terms, one step up from that is WDM, which will give you those options, but gdm is the best all around.

I've done many,many server/command-line build ups and always use gdm(kdm for kde related builds) gdm will work with all WM's.

---

### Post by wafer on 2007-01-10
Ok, I'll give it a shot.  I'm just a little worried about throwing away some of my limited system resources on a login manager.  The How-to I referenced in my first post made me more than a little tentative about using GDM as a login manager.

What exactly would I need to do here?  Would these be the commands in Xterm and in this order?

$ sudo aptitude purge xdm (or aptitude remove xdm?)
$ sudo aptitude install gdm

Thanks for the quick reply.

wafer

---

