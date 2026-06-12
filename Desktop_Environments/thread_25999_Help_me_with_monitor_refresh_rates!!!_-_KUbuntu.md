---
title: "Help me with monitor refresh rates!!! - KUbuntu"
date: 2005-04-11
forum: Desktop Environments
---

### Post by Cool_dude_Prav on 2005-04-11
I am sorry to re-start a new topic with the same issue, but no one seems interested in replying to that one...

[This is old one](http://ubuntuforums.org/showthread.php?t=24264)

Plz help me!!!

I have a Samsung SyncMaster 773s and KUbuntu shows me a refresh rate of just 65 Hz whereas i have it as 95 Hz in Windows,

I find it extremely diffi. to work on KUbuntu!!! Plz help me...

P.S: I already tried dpkg-reconfigure xserver-xorg (shows 640 * 480 after that which is worse)

---

### Post by dodger on 2005-04-11
in the KDE control center should be an option somewhere where you can set the resolution and the refresh rate.
if your preferd settings do not show up, make sure that these settings in /etc/X11/xorg.conf are set correctly for your monitor:

        HorizSync       xx-xx
        VertRefresh     xx-xxx

you should find the correct values by searching for your monitor on google.

---

