---
title: "- HELP - My desktop is gone"
date: 2017-11-30
forum: Desktop Environments
---

### Post by romzy on 2017-11-30
Using (one of?) the latest version of Kubuntu and my desktop just disappeared leaving just a black screen at the back
I have just access to a web page I opened before it bugged 
I tried to reboot, shut down etc.. it does nothing, when I login I can access to the desktop for a second and gone, not enough to open a Konsole, ctrl + alt + t doesn't work, and I can't reboot unity using ctrl+alt+F1 (who works) even if I use my login ID and a correct password (I typed it in face of login to be sure)..

If someone could help me...

---

### Post by blackbird34 on 2017-11-30
It sounds like the window manager crashed. This is the part of the  system that puts the bar at the top of the window with its name (window  title) and handles all the system keyboard shortcuts like Ctrl+alt+T.

Did you remove any packages/ programs/ applications accidentally? If you did maybe you could try to open a terminal via Ctrl+Alt+F1 and type ```
sudo apt install kubuntu-desktop
``` to try to bring them all back (this reinstalls the main suite of applications for Kubuntu). 

Also, you mentioned both Kubuntu and Unity, did you install multiple desktop environments? They sometimes conflict with each other and cause problems (even more so if you add one of them from a PPA), because they try to modify things in different ways... 

Could you give us more detail on your problems? 

For future reference if your system crashes like this there is a "magic" combination to force a system restart without messing up all the system files: 
Alt + Sysreq + [in this order, a few seconds between each one] R - E - I - S - U - B  .  
Hold down the Alt and Sysreq keys the whole time. Sysreq is probably marked as "Print Screen" but it occasionally varies. 
[https://en.wikipedia.org/wiki/Magic_SysRq_key#Uses](https://en.wikipedia.org/wiki/Magic_SysRq_key#Uses)

---

### Post by romzy on 2017-11-30
I've red on a forum that I might need to restard unity or something like this using the ctrl+alt+F1 nothing more, I have only one desktop environment.
I would love to do the command you gave me but I can't pass the login session of ctrl+alt+F1 even with my session id (on my computer) and the right password (the one I use to log in on my session)

I don't know what more to say...
But thanks a lot

---

### Post by coffeecat on 2017-12-01
Not a chat thread.

*Thread moved to **Desktop Environments**.*

---

### Post by vasa1 on 2017-12-01
> **blackbird34 said:**
> ... 

Also, you mentioned both Kubuntu and Unity, did you install multiple desktop environments? They sometimes conflict with each other and cause problems (even more so if you add one of them from a PPA), because they try to modify things in different ways... 

...
^^^ +1.

If you want to try out different desktop environments, be prepared for odd things happening.

Do a clean install of whichever system you want and try out other systems using Live USBs or virtualization.

---

### Post by nibal on 2017-12-01
I'm using Ubuntu, not kubuntu. 
<Ctrl>-<Alt>-F1 will open up a console for recovery.
From that console you can check your /var/log/syslog for any segfaults and post them here.
Also check for any files under /var/crash. They refer to corrupted/missing packages for that segfault. Post the ls output here.
If it were ubuntu, I would say it sounds like a compiz segfault at libnux-graphics. Compiz is not well written and instead about
complaining about missing packages, it just crashes:( But it is Kubuntu and I don't know if it uses compiz.

HTH
Nikos

---

### Post by romzy on 2017-12-01
I do not have many desktop environments..
and when I use ctrl+alt+F1 it asks me for a login and a password that doesn't match with the one I use to log in my session

Sorry if it's not a chat thread btw..

---

