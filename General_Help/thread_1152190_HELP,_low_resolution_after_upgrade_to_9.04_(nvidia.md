---
title: "HELP, low resolution after upgrade to 9.04 (nvidia drivers not working)"
date: 2009-05-07
forum: General Help
---

### Post by rcopper on 2009-05-07
After updating to Ubuntu 9.04, and trying to log in I received the following error:
(EE) unable to find a valid framebuffer device
(EE) NV (0) failed to open framebuffer device
etc...

after that being offered to go to the low resolution mode (800x600 or even worse instead of the needed 1280x1024).

I tried installing pretty much every possible combination of drivers in synaptic nvidia-glx 180, 173... also the drivers from nvidia website, then tried the envyng, and so forth.. nothing worked properly - the drivers were finding a CRT screen.. with a low res..

in several occasions there were some drivers appearing in the list of hardware drivers but couldn't activate any of those (180 recommended, 173, etc)

I also tried edditting the xorg.conf by adding a modline there with the required resolution but it didn't work either... however I'm not really sure I did everything right with this one..

The thing is that in Ubuntu 8.10 everything was working fine (can't remember which were the drivers that worked)

I have a LCD screen Samsung SyncMaster 721, with nVidia GeForce 6150 SE nForce 430 graphic card.

Can somebody help me please?

PS: I've tried to follow the advices given at [http://ubuntuforums.org/showthread.php?t=1136343](http://ubuntuforums.org/showthread.php?t=1136343) but nothing seems to work.. :(

---

### Post by tarverator on 2009-05-08
I am having a similar problem in Xubuntu. Upgrading 8.10 --> 9.04 knocked out the high-res video on a Toshiba M30 laptop: 01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 64M] (rev a1)

Neither can I remember how I had it working in 8.10...

I tried downloading the restricted drivers via the hardware drivers GUI,

I tried manually re-installing NVIDIA-Linux-x86-96.43.11-pkg1.run (which worked on 8.10, but comnplained about missing sources in 9.04),

I tried restoring the pre-upgrade xorg.conf,

I tried xfix (from the recovery menu),

and I tried:
dpkg-reconfigure xserver-xorg

...all to no avail (though not necessarily in that order).  Maybe one of these would work if one of the others didn't make it worse?

---

### Post by rcopper on 2009-05-10
well, I have to say I managed to fix everything after all - by following (again) the How-To at the page [http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400) with the exception thast I used the stable NVIDIA-Linux-x86-180.51-pkg1.run drivers from Nvidia website.

---

