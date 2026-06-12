---
title: "Akh, Screen Resolution"
date: 2007-10-05
forum: Desktop Effects &amp; Customization
---

### Post by Locutus_of_Borg on 2007-10-05
I had been running just fine on 1024 x 768 but for whatever reason decided to change it to 1280 x 800 since that is what my monitor is capable of handling.  I installed 915resolution, restarted, and changed the screen resolution.  I noticed after a while that compiz fusion was no longer working and restarted again.  I could only boot to a black screen with blinking cursor, so I rebooted again into recovery mode and manually edited my xorg.conf file so I could see a desktop again, only now, trying to set my resolution back to 1024 x 768 I find that the lowest I can set it is 1280 x 800.

I wouldn't mind if compiz fusion worked, but it doesn't.  Any suggestions?

Thanks.

:confused:

---

### Post by Locutus_of_Borg on 2007-10-05
nevermind, fixed it through dpkg-reconfigure -phigh xserver-xorg

sorry for wasting the time of whoever might have read this


though i would like to use compiz at the higher resolution, not sure why it stopped working and wouldnt let me boot in the first place..



edit: must have screwed something up the first time, because now everything is working fine at 1280 x 800

---

