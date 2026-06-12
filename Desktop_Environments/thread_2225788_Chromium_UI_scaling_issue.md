---
title: "Chromium UI scaling issue"
date: 2014-05-23
forum: Desktop Environments
---

### Post by epitaph2 on 2014-05-23
Hi,

I'm on a fresh KUbuntu64 install, and noticed that the UI for chromium-browser is absolutely huge. My display is 1920x1080--not super-high DPI. But somehow chromium seems to think it is. Compare Firefox and Chromium, both at 100% zoom:

[http://imgur.com/lCQAOAr](http://imgur.com/lCQAOAr)

Note that it's not just the content, but the full UI. Menus are unworkable as most of the text is occluded. Any ideas how to fix this?

Thanks!

---

### Post by bapoumba on 2014-05-24
Have you tried <ctrl><-> to lower the zoom ?

---

### Post by vasa1 on 2014-05-24
Or Ctrl+0 (zero) to get the "default" zoom.

---

### Post by epitaph2 on 2014-05-24
Thanks, but the point is that it affects the *whole UI, *not just the rendering engine. As you can see, the fonts in the title bar, tab bar, menus etc. are also massively oversized.

Zooming to normal character sizes requires me to be in the 25% range, and text rendering really takes a dive. So this is not an option.

At this point I'm mostly wondering whether it's a Chromium-specific issue and should file a bug report with them, or whether it's something to do with KDE/qt4/?

---

### Post by vasa1 on 2014-05-24
If you're on Chromium 34, I understand that that version (and Google Chrome 35) have Aura instead of GTK+. Maybe that could be the issue.

I'm on Chrome 35 and don't have much of a problem but my screen is only 1366x768. BTW, this is LXQt on Lubuntu 14.04 so I'm assuming it's currently qt4.

---

### Post by bapoumba on 2014-05-24
Any extension or plugin ?
Please try to make a new user in Chromium to see if it is something in your user profile.

---

### Post by epitaph2 on 2014-05-24
The user profile is out-of-the-box after apt-get install chromium-browser. I just removed ~/.config/chromium but the problem persists.

---

