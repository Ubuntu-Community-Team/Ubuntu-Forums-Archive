---
title: "No Desktop After Upgrade from Gutsy to Hardy"
date: 2008-07-30
forum: Desktop Environments
---

### Post by nojoeblow on 2008-07-30
Hi

I just tried to upgrade from gusty (via internet) to hardy but the installation hung near the end.
I waited for 30 minutes but it wouldn't respond and eventually had to shut down normally.
On reboot it started in low graphics mode.
I got a login screen and tried to log in as normal.
After login, it loads the default ubuntu desktop background colour but no desktop. The only thing on the screen is the mouse cursor, which is active, but that's it.

Any ideas how to get the desktop back and get the system to check the installation for anything that caused it to stop and fix it?

Thanks

---

### Post by steveneddy on 2008-07-30
The best thing would have been to do a complete reinstall.

Have you tried rebooting and trying the safe boot option?

---

### Post by nojoeblow on 2008-07-30
Thanks steveneddy, I just tried safe boot and selected dpkg - fix broken packages.
It processed some packages and has stopped at the same point as when it hung during the upgrade: 

setting up locales (2.7.9-4)
Generating locales...
 en AU.UTF.....

The cursor has been just sitting there for the past 10 minutes

I would prefer to work through this issue to see if I can overcome it as I'm a bit aprehensive about re-installing. I don't want to overwrite my home directory or lose printer settings etc. Are directory structures and settings retained in a re-installation?

Anyone have any ideas to get past the issue with it hanging while trying to generate locales?

---

### Post by Cygoku on 2008-07-30
Usually, before upgrading to Hardy from any version, you should always uninstall video card driver.  

So try this in a terminal safe mode  : 

sudo apt-get install --reinstall libgl1-mesa-glx

Cygoku

---

### Post by nojoeblow on 2008-07-30
Thanks Cygoku. I ran the command but it returned "dpkg was interrupted you must manually run "dpkg --configure -a" to correct the problem.
I did that but it has again hung at the locales issue.

---

### Post by nojoeblow on 2008-07-30
I found this thread about the same issue I was having.

[http://ubuntuforums.org/showthread.php?t=865679](http://ubuntuforums.org/showthread.php?t=865679)

I gollowed siberoptik's instructions in post #3 and it worked a treat

---

