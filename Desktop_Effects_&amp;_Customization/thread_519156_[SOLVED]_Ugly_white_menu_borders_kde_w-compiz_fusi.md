---
title: "[SOLVED] Ugly white menu borders kde w-compiz fusion"
date: 2007-08-06
forum: Desktop Effects &amp; Customization
---

### Post by maestrobwh1 on 2007-08-06
All of my menus have ugly white borders and also, those borders frequently cut off the lowest menu item.  I attached a screen shot so that anyone who might be able to help me switch from beryl, which looks fantastic for me, to compiz fusion, as that seems to be where things are heading.

I can't seem to see in settings where to get rid of it and also, I have a similar streak at the bottom of my screen between the desktop and bottom panel.

For my main menus, nothing gets cut off, but if I right click anything, those menu's are even "uglier."

I am actually unable to use compiz if I can't get rid of this... it irritates me that much.

---

### Post by jimbren on 2007-08-07
Have you installed emerald?

```
sudo apt-get install emerald beryl beryl-manager emerald-themes
```

It will give you some spiffy themes and window cecorations.

thanks,


jimbo

---

### Post by maestrobwh1 on 2007-08-07
Actually, I do have those packages installed and I used beryl way before compiz.  If I use the beryl manager to launch compiz, I get that ugly thing I mention and you can sue.  Using Emerald with compiz... I get no window decorator and have to use the "compiz kde dekorator"

Oddly, compiz on my feisty install looks fine.

If I switch back to beryl, it all looks fine.

---

### Post by maestrobwh1 on 2007-08-08
Does anyone else get this... it doesn't look like it is supposed to be this way, as the borders are "flat" and don't appear to be a 3-d artifact, or the border is an artifact that is not rendering properly.

It only appears on my Gutsy install with compiz.  It does not do this with my Feisty install.  Same machine.

Beryl works fine, btw.

Edit after "playing" around

If I change the window decorator to Compiz-kde-decorator using the little beryl tray icon, then change to compiz, I get a minor crash in kde (just a pop up), Compiz loads, but with no window decorator, THEN if I select emerald, that decorator works.  I HAVE to do it in this order... and compiz looks... well, like beryl

---

### Post by ethan961 on 2007-08-10
Well, Gutsy is Gutsy, an alpha. Anyway, Looks to me like your shadows are not rendering properly. Does this appear on normal windows too? Also, your feisty and gutsy packages are probably different versions, this might have been fixed in the latest git version. Emerald should have no effect on the shadows, as compiz itself does that.
Hope you get it working without that annoying procedure.
> **maestrobwh1 said:**
> Does anyone else get this... it doesn't look like it is supposed to be this way, as the borders are "flat" and don't appear to be a 3-d artifact, or the border is an artifact that is not rendering properly.

It only appears on my Gutsy install with compiz.  It does not do this with my Feisty install.  Same machine.

Beryl works fine, btw.

Edit after "playing" around

If I change the window decorator to Compiz-kde-decorator using the little beryl tray icon, then change to compiz, I get a minor crash in kde (just a pop up), Compiz loads, but with no window decorator, THEN if I select emerald, that decorator works.  I HAVE to do it in this order... and compiz looks... well, like beryl

---

### Post by maestrobwh1 on 2007-08-11
I more or less fixed it with doing some of this.  [http://ubuntuforums.org/showthread.php?t=511389](http://ubuntuforums.org/showthread.php?t=511389)

The user Menox has been really helpful so anyone else with questions might want to that thread.

I could not use all of the method listed in the beginning of the thread (using the .profile script in my home folder didn't launch it and I had no keyboard access), so I did make a bash script called "startconfig in my /usr/bin like mentioned there and then made a desktop item for launching that item.  After testing it, I then put a copy of it in my /.kde/Autostart menu. 

 For Gutsy, it seems to launch compiz fusion with the emerald decorator 100% of the time.  Although I never had the border problem in feisty, it was never that stable.  Half the time during launch, the emerald decorator doesn't load (it would try to load the kde decorator and crash emerald) so I would have to click my created desktop item again.  It also just seems to run in a more "cumbersome" manner in Feisty.  I do have compiz fusion installed in Feisty using a 3rd party repo.  Apps also just mysteriously close when compiz is running under Feisty for me.  

Not to be even more verbose in my reply, but My current Gusty install was an upgrade from Dapper, to Edgy to Feisty, and now Gutsy.  I alternate between upgrading each partition install when a new alpha comes out.  This one [Gutsy] s a true Gem.  I never had a "crash" and anything that stopped working started working again in a day or two.  The biggest issue is when apt adept and synaptic didn't work... downgraded apt using a *deb package I found and then did an update and upgrade within a day and all was good.

---

### Post by mithbuntu on 2007-10-23
I have this problem myself and don't know when it first appeared or how you fixed it.  That thread  you suggested seems way too cumbersome for something that seems like a tiny fix.

What are those ugly white menu borders from?

---

### Post by explemonk on 2007-10-24
I solved it by turning off drop shadows on the KDE menus.

K-Menu -> System Settings -> Appearance -> Style -> Effects Tab -> Uncheck "Menu drop shadow"

---

### Post by maestrobwh1 on 2007-10-24
Wow, that seems simpler than what I did, but I also had an issue with emerald crashing on start, so my more complicated method also fixed that.

---

