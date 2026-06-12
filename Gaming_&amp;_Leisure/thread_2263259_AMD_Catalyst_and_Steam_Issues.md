---
title: "AMD Catalyst and Steam Issues"
date: 2015-01-30
forum: Gaming &amp; Leisure
---

### Post by IvantheDugtrio on 2015-01-30
So I'm having this conundrum.

First I would start with a fresh install of Xubuntu 14.10, install steam, log into steam, then install catalyst 14.12 first using the .deb package from AMD's website. That doesn't work so I follow the Catalyst Linux Wiki and make a package from the zip archive and install all the dependencies they list. I install and run "amdconfig --initial -f". When I reboot I get stuck on a black screen. I try switching between my xorg.conf backups in recovery mode but it doesn't help. The only way to get back to the desktop is to purge fglrx and reinstall the open source drivers

Next I do another fresh install of Xubuntu 14.10, install catalyst according to the wiki. I reboot and it works fine. Then I install steam and it won't launch. It tells me it segfaults due to some .so files. 

People who have had this issue say to install Steam first but that doesn't work for me. What should I do? Prior to this I've used the open-source drivers for some time but I would get some weird crashing and eventually Xfce would stop rendering windows in 3D. It's really weird. 

System specs:
Intel Core i5 3570k
ASRock Extreme4 Z77
Corsair 8GB DDR3 1866
HIS HD 7870
Crucial 256GB MX100 SSD

---

### Post by mastablasta on 2015-02-02
any specific reason why you need catalyst from AMD and why not just use the ones found in your Ubutnu/Xubuntu additional drivers package?

---

### Post by IvantheDugtrio on 2015-02-02
The additional drivers package doesn't allow me to install it for some reason. It just has the proprietary driver boxes greyed out. I've also installed Ubuntu restricted extras if that has anything to do with it. 

I'll try again when I get home.

---

### Post by mastablasta on 2015-02-03
interesting. try method in 2.1: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

copy & paste the commands.

---

### Post by oldrocker99 on 2015-02-03
Not flaming, but, when I see three AMD users' ATI problems, I'm glad I have nVidia.

There's a reason that practically every Linux forum recommends nVidia. Its FOSS drivers are pretty bad, while its proprietary drivers are pretty good. This is the opposite of ATI drivers.

---

### Post by QIII on 2015-02-03
This is not a problem with the AMD driver. Most problems with the AMD driver stem from not installing it properly.  That's why I put section 2.1 in the wiki.

Note that the OP says it works fine before installing Steam.

Steam does not play well with AMD drivers initially.  Steam does have to be installed first, but it's not quite as simple as that.

Here's the trick:

Uninstall Steam and the AMD/ATI driver to have a clean start.

Reboot.

Install the AMD/ATI driver per 2.1 in the wiki link in my sig and reboot.

Install Steam and attempt to update it.  It will throw an exception.

Uninstall the AMD driver and reboot.

Reinstall the driver and reboot.

Finish updating Steam.

This is an issue with Steam, not the AMD driver.

---

### Post by IvantheDugtrio on 2015-02-06
Thanks guys for all the replies. I've done some additional testing with the Additional Drivers tab from fresh installs.

So installing from there would give me problems on reboot. I've tried fglrx and fglrx-updates and both seem to be dysfunctional after installation. Boot up hangs for some reason. 
After switching back to the open-source driver I reinstall steam and try launching a game, only to tell me my system doesn't support a new enough version of OpenGL. 

I should beg Gaben to make a 64-bit Steam Linux client so we don't have to bother with 32-bit libraries. 

I'll follow the last post and report how it goes. Also should I use aticonfig or amdconfig?

---

### Post by R33D3M33R on 2015-02-07
Try this with OSS drivers: [http://askubuntu.com/questions/506349/opengl-glx-context-is-not-using-direct-rendering-which-may-cause-performance-pr/538907#538907](http://askubuntu.com/questions/506349/opengl-glx-context-is-not-using-direct-rendering-which-may-cause-performance-pr/538907#538907)

---

