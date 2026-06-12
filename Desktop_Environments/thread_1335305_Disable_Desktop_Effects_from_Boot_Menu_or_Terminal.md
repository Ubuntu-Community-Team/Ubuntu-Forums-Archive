---
title: "Disable Desktop Effects from Boot Menu or Terminal"
date: 2009-11-23
forum: Desktop Environments
---

### Post by rezapiri09 on 2009-11-23
I'm running Karmic Koala on a Toshiba and I made some graphical changes to my desktop environment this last week.  I was running AWN and I switched over to GNOME-DO.  After a couple of days of running GNOME-DO I enabled the wobbly windows, etc for Desktop Graphics to see if it had the same problems as AWN did with desktop graphics.  It ran well for a couple of days then crashed out upon the fourth re-boot. Now my screen draws a blank after Ubuntu loads from the Grub menu.  The white ubuntu logo loads up but the name "ubuntu" with the loading bar doesn't load on the next screen- the screen just goes blank.  I have searched numerous forums to find a solution and can't seem to get the correct instructions to figure out how to disable desktop effects from the grub menu or terminal.  Could someone please help?  I use this computer for all my work needs, so I need to get this thing going before I get too swamped this week.  Thanks guys!

---

### Post by carml on 2009-11-23
Try the recovery option at startup: 
1. you have a dual-boot machine? Simply choose the second entry from the    
   top of the screen.
2. you have only Ubuntu installed? Press ESC to enter the menu and select  
   the second entry from the top of the screen.

Once you've done what I say before, choose reconfigure X or soething similar
(I don't remember exactly at the moment), it will load your default graphic options and so it should resolve your problem.
Let us know if it works :-).

---

### Post by rezapiri09 on 2009-11-23
Yes I run a dual boot and I have tried running the second option and the result:

Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT!@ /dev/disk/by-uuid/fcf0f43-1beb-4786-bc8a-256511095cdb does not exist dropping into a shell!

BusyBox v1.13.3 (ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)

(initramfs) _

Ubuntu will not load, but I can run built in commands at this point.  What does this mean and where do I go from here?

---

### Post by carml on 2009-11-23
If I understood well you chose to enter as root,maybe I'm wrong.
When you choose the recovery option,you should see these options
(I'm going along my memories):

boot normally;
try to fix broken packages;
droop to root shell;
try to fix X server.

I'd suggest you to try to fix broken packages and in order to do that you need a functioning internet connection,the installer will try to download again all the installed packages and will fix the broken ones if succeed.
If it coudn't fix,you can always choose to try to fix the X server or boot as root and force the reinstallation of the graphic environment.
If no one of these functions you can still try to fix the system using the LiveCD of Ubuntu.

I hope you can fix your problem, post here if you need more explanations or if you have doubts. :-)

---

### Post by rezapiri09 on 2009-11-23
I am at the root@ubuntu:~# prompt

How do I force the reinstallation of the graphic environment?

---

### Post by carml on 2009-11-24
> **rezapiri09 said:**
> I am at the root@ubuntu:~# prompt

How do I force the reinstallation of the graphic environment?
First of all try as root to type ```
apt-get update && apt-get upgrade
```,if this don't resolve,you have always to enter as root and type ```
apt-get install gnome-base
```,if I recall right it should reinstall the base for the environment.
Maybe you have first to uninstall, if this is the case you have first to type ```
apt-get remove gnome-base
```.
To be more sure wait to see if someone corfirm what I wrote above,because maybe there's a solution I'm not aware of.

---

### Post by rezapiri09 on 2009-11-29
I tried that route but had trouble trying to find the correct root prompt.  I made a live cd of karmic and wiped slate clean. Luckily I had back ups of most files. I have spent the holidays re-installing software, VMs, Crossover, and MS Office. Lesson learned: don't try to over exceed awesome graphic effects with ubuntu and always back up files.

---

