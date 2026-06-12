---
title: "Trim down xubuntu 7.10"
date: 2009-02-10
forum: General Help
---

### Post by dreamersrevenge on 2009-02-10
I'm currently working on an xubuntu laptop based digital picture frame. The specs aren't too great but it's functional (including wireless, the biggest thing I was having problems with) enough running xubuntu 7.10 on 64mb ram with a 6gb hard drive. It's a Celeron 600 so it isn't exactly a powerhouse. My question is, what services/applications can I uninstall to speed up the boot time a little, and eliminate altogether to save space? I'm going to remove the obvious apps, such as office/productivity, multimedia, and games, however I'm gonna add a wireless manager and either use feh with some scripts to run the slideshow, or the xslideshow screensaver and set it to run after one minute of idle time. Any suggestions?

---

### Post by ScarySquirrel on 2010-04-23
Check to make sure that the firewall is disabled. Also, you can try disabling Python. 
Make sure that all accessible disks have a linux compatible format, like ext3, to squeeze out a few more megabytes. 
Ditch the clock, too. 
Disable the mixer daemons. If you see anything with "mix" or "vol" in it in the process list, look it up on google. If it's sound related, ditch it. 
Any "wallet" daemons may also go, too. I'd look into an alternative to xfce's default network daemon, too. 
There's also a package which shows you what things are running at startup, but I don't remember it's name. search around in synaptic for something with "startup" or "init" in it, and if it says "manage which applications appear at startup" or something like that, get it and go hog-unwiled. 

I have spoken.

---

### Post by ScarySquirrel on 2010-04-23
Also, using a desktop environment for something this specialized seems unwise. I suggest looking into Fluxbox. Fluxbox might not cut off the whistle, but at least the bell; 
[https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)

---

