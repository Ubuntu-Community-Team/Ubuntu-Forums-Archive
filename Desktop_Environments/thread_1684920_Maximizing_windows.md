---
title: "Maximizing windows"
date: 2011-02-09
forum: Desktop Environments
---

### Post by ndyguy on 2011-02-09
After updating recently, I can't maximize windows properly. There is a gap on the left and top of the window. Any ideas how to fix this?

---

### Post by inobe on 2011-02-09
what did these updates consist of, any video driver stuff?

i'm guessing that previous to the update your screen wasn't at full resolution, is this your first update and have you restarted since?

---

### Post by ndyguy on 2011-02-11
> **inobe said:**
> what did these updates consist of, any video driver stuff?

i'm guessing that previous to the update your screen wasn't at full resolution, is this your first update and have you restarted since?

I don't recall the updates. I believe my screen was full resolution, I've updated many times in the past, and I've restarted several times. It seemed to happen after Compiz was updated/added to desktop in top left. I thought it might just be a setting, but can't find it.

---

### Post by inobe on 2011-02-11
you do have an old version of kde on there judging by the icons..

a lot has changed, have you considered upgrading to kde 4.6?

i know for a fact that the last upgrade fixed over 20,000 bugs.

you can do this if you have kubuntu 10.10 installed.

this is all i can think of unless you wish to reset your desktop to defaults.

edit: check the differences in kde 4.6 [http://www.kde.org/announcements/4.6/plasma.php](http://www.kde.org/announcements/4.6/plasma.php)

---

### Post by ankspo71 on 2011-02-12
> **ndyguy said:**
> After updating recently, I can't maximize windows properly. There is a gap on the left and top of the window. Any ideas how to fix this?

Yeah I think so. It looks like to me that you have 2 extra panels added to the top left corner of your screen and the reason why you you can't maximize your windows is because those panels are set as "always visible". One is actually a "top" panel (moved to the left) blocking your window from maximizing up, and the other panel is a "left" panel (moved to the top) blocking your windows from maximizing left.

If you don't want those panels simply right click on them and then click "remove this panel". Edit: Just so you know ahead of time, this could be a result of a bad configuration file in your hidden .kde settings folder located inside your home folder (/home/yourname/.kde/share/config/*). It could probably be plasma-desktop-appletsrc or plasma-desktoprc. Try removing the panels by right clicking on them first though.
 
Hope this helps.

---

### Post by ndyguy on 2011-02-12
> **ankspo71 said:**
> Yeah I think so. It looks like to me that you have 2 extra panels added to the top left corner of your screen and the reason why you you can't maximize your windows is because those panels are set as "always visible". One is actually a "top" panel (moved to the left) blocking your window from maximizing up, and the other panel is a "left" panel (moved to the top) blocking your windows from maximizing left.

If you don't want those panels simply right click on them and then click "remove this panel". Edit: Just so you know ahead of time, this could be a result of a bad configuration file in your hidden .kde settings folder located inside your home folder (/home/yourname/.kde/share/config/*). It could probably be plasma-desktop-appletsrc or plasma-desktoprc. Try removing the panels by right clicking on them first though.
 
Hope this helps.

Thanks ankspo71! You were right; I don't know how, but I got two extra panels in the top left.

Thanks also to inobe for your suggestions.

---

### Post by inobe on 2011-02-12
thought i seen it all :lol:

---

