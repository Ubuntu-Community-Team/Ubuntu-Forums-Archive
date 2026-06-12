---
title: "kdm not running"
date: 2008-04-26
forum: Desktop Environments
---

### Post by santhosh23 on 2008-04-26
Hi,

I recently upgraded to Kubuntu-hardy, i not able to load the desktop successfully, i get the login manager and after i login it load the kde 4.0 splash screen and gives me a blank and the screen stays the same for a longtime.i went to rescue mode and tried dpkg --reconfigure however that did not resolve the issue. i could see that kdm is not running so i tried start it from a diff from console still the same, i am not if the settings in xorg.conf is screwed up or is the kdm, i then i started comparing the files in kde3 to kde4 and found the there was not kdmrc file under kde4.

any advice would be apprecaited.

---

### Post by santhosh23 on 2008-04-26
To my observation is found that there not files in /etc/kde4/kdm expect kdm.options and after lots of google i found that this is bug.

[https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/165274](https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/165274)

---

