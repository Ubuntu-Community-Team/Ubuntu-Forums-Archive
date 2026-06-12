---
title: "Screen blacking out after a few mins of no use..."
date: 2021-05-13
forum: Desktop Environments
---

### Post by dbee on 2021-05-13
I figured the screensaver must be kicking in. So i disabled screensaver. Then I disabled the power saving mode. After that I configured LightDM GTK+.

After that didn't work I tried looking for the xorg.conf file which xubuntu doesn't use anymore.

Then i opened Sessions and Startup and disabled Screensaver and Screenlocker on startup.

Then i restarted xubuntu.

Screen still going black after a few mins. I'm using GNOME.

BTW This is a brand new screen for the laptop ThinkPad. I broke the other one.

> 
$ uname -a
Linux dara-ThinkPad-Laptop-11-y0XX 5.4.0-73-generic #82-Ubuntu SMP Wed Apr 14 17:39:42 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux


---

### Post by dbee on 2021-05-14
Maybe i should create an overriding xorg.conf file and add some config variables to it?

---

### Post by dbee on 2021-05-18
Does anyone have any ideas here?

My zoom classes keep blacking out...

---

### Post by dbee on 2021-05-19
It seems to be working fine now.
 
I used xset to turn off power management - dpms and turn off screensaver...

> 
xset s off && xset -dpms


I'll post back here if anything changes... thanks

---

