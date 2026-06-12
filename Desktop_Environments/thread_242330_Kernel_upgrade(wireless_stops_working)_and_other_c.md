---
title: "Kernel upgrade(wireless stops working) and other concerns"
date: 2006-08-23
forum: Desktop Environments
---

### Post by neo_reloaded on 2006-08-23
Running Dapper "LTS" and I am "nervously" happy to see the bulk of updates coming down every day. I have following issues and rants:

1) Updated to 2.15.26 i686 kernel - and wireless stopped working. Its a known issue and I dont see any update coming. So still running i386 2.15.25 kernel.

**[COLOR="Red"]Is there a fix for this?[/COLOR]**

2) Recent updates - libvte and xorg - why do we have to go through painful updates as these? which gives out threatening messages as "Cannot update any package, package database index broken" etc? May be it is just me as I am trusting dapper with my expensive hardware( read 2K)

**[COLOR="Red"]Is anybody monitoring such upgrades?[/COLOR]**

3) The chunk of upgrades and debs coming via the internet. 

**[COLOR="Red"]Are these upgrades leaving any "residue" in my computer eating up diskspace, which I can reclaim?[/COLOR]**:confused: 
Once if I successfully go to i686 kernel, [COLOR="Red"][B]can I run a 
sudo apt-get remove linux-386[/B][/COLOR] ?

---

### Post by neo_reloaded on 2006-08-23
A quick search shows a lot of people haveing issue with wireless after kernel upgrade.

I assume this is still unresolved!!!

---

### Post by anindya_m on 2006-08-23
Did you also upgrade the restricted modules package? This contains the wireless drivers for many cards.

---

### Post by anindya_m on 2006-08-23
Check for example this thread:

[http://www.ubuntuforums.org/showthread.php?t=240466](http://www.ubuntuforums.org/showthread.php?t=240466)

---

### Post by neo_reloaded on 2006-08-24
Thanks!
I had to follow [http://www.ubuntuforums.org/showthread.php?t=38972&highlight=atheros](http://www.ubuntuforums.org/showthread.php?t=38972&highlight=atheros)

Wierd though, that an upgrade can cause a lot of grief.

Now, is it OK to remove i386 completely from my PC?
:)

---

