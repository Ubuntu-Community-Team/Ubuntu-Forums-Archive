---
title: "How do I stop icons from moving on every re-boot?"
date: 2015-04-28
forum: Desktop Environments
---

### Post by Mike_Walsh on 2015-04-28
Evening, everybody.

I'm using Xubuntu 14.04.2, a recent install. Every time I re-boot my machine, whether from a cold start OR a warm re-boot, my desktop icons all reset themselves against the left-hand edge of the screen. I've investigated every possible way of preventing this from happening, but can't find any way of actually 'locking them', or of making them 'sticky'.

Would any kind soul be able to point me in the right direction on this one? Advice will be, as always, appreciated.


Regards,

Mike. :)

---

### Post by Keith_Helms on 2015-04-29
That's odd.   I normally leave my icons left-adjusted on my Xubuntu 14.04.2 system, but just to see what would happen I dragged some of them out into the middle of the screen and rebooted.  They stayed where I left them.   I went into settings manager and desktop and turned on display icons for home, filesystem, and removeable devices, which I usually leave turned off, and those icons popped up in the "holes" where I had dragged my icons out of.   I rebooted and everything was still in the same places.  I tried changing screen resolution to the point where some icons disappeared off the edge and when I reverted to full resolution, they were back where I left them.

That being said, I googled the issue and there do seem to be a lot of similar problem reports and at least a couple of bugs on launchpad.  It must be some combination of settings, drivers, configuration, whatever that causes it to hit some systems and not others.  I don't think you'll find any "stop doing that" option for this.   It's more likely you'll find that it happens in combination with something you have set or something you do while using the system.  Dual monitors or games that change the screen resolution or who knows what.  

If you want to apply the scientific method to this, you could do a fresh install, don't change any settings, create an icon in the middle of the desktop and see what happens.  If it stays put, then make your tweaks to the system and retest after each one.   If it still moves, then it must be something unique to your hardware or the drivers for it.

---

### Post by Mike_Walsh on 2015-04-29
Hallo, Keith; thanks for your observations.

I'm kinda thinking along the same lines myself! I have Xubuntu Trusty on both my elderly Dell laptop and my equally elderly Compaq Presario desktop. It doesn't happen on the Dell, where it's the sole installed O/S. However, on the desktop, I have a couple of 'Buntu installs, and 3 or 4 'Puppies'.....plus I'm always 'experimenting' on the PC. 

Sometimes it'll happen, sometimes it doesn't; it doesn't seem to be predictable at all. It's not a problem; I can live with it, as I only have a half-dozen icons on the desktop anyway. Just a wee bit annoying..!


Regards,

Mike.

---

