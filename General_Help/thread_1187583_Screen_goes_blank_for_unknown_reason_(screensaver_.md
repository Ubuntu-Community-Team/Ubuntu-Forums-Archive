---
title: "Screen goes blank for unknown reason (screensaver related?)"
date: 2009-06-14
forum: General Help
---

### Post by Mattaus on 2009-06-14
Hi all,

I'm busy running 9.04 and using it for a HTPC (XBMC and MythTV).

However the screensaver activating all the time was kind of annoying so I thought I killed the thing with the following:

> 

sudo killall gnome-screensaver

gconftool-2 --type boolean -s /apps/gnome_settings_daemon/screensaver/start_screensaver false

sudo chmod -x /usr/bin/gnome-screensaver


I pulled all that from this thread:

[http://ubuntuforums.org/showthread.php?t=195557&highlight=kill+gnome+screensaver](http://ubuntuforums.org/showthread.php?t=195557&highlight=kill+gnome+screensaver)
[B]
However[/B] (and I'm not sure on the exact times here) every 3 minutes or so the screen goes blank. It doesn't just suddenly go blank...it fades as if its a screen saver. This is further backed up by the fact that when I wiggle the mouse or click a button the screen comes back to life. 

I have an odd feeling this may be causing another problem I'm having in XBMC (The whole system locks up while watching a video inside XBMC, at the same sort of intervals).

Have a ruined something with those commands above? Does anyone know what is going on here? I had done this on a previous build that was using Nvidia graphics and never had this problem. (this new machine is using ATI).

I'm no expert so your help would be greatly appreciated. I can provide further details if this will help in anyway.

Cheers.

---

### Post by nandemonai on 2009-06-14
Have you tried disabling the screensaver in System -> Prefs -> Screensaver ?

Also you may want to check out power management.

---

### Post by Mattaus on 2009-06-14
Hmmm, no I have not disabled it under system settings but I thought doing what I did would kind of make it hard to run now lol.

Power management is a good place to check...I had issues previously on a Windows box because power management was crewing my video playback and it took me ages to realize so you'd think I would have thought about that already. Though like I said I never had this problem on the old motherboard so why would it happen now? Different hardware granted, but still odd.

I will check it out once I'm home tonight!

Thanks for the reply.

---

### Post by Mattaus on 2009-06-15
I tried everything and nothing seemed to fix it so I resorted to simply re-installing the ATI drivers and what would know its fixed :D

I'd love to know what happened in the first place. Maybe I broke something in my tinkering and re-installing fixed it?

---

