---
title: "Mirrored monitor doesn't show mouse pointer"
date: 2009-06-05
forum: General Help
---

### Post by Vunutus on 2009-06-05
I have a HP 2133 netbook. It has a VGA out port which is used for mirroring the display to another monitor (since it has a tiny screen that's hard to see by other people than the one using it). I hook a monitor up to it and get the mirroring working correctly, but there is no mouse pointer. It shows up fine on the real laptop screen, but does not show on the mirrored display. This makes it pretty impossible to close the laptop lid and use only the mirrored monitor. Whenever I hover the mouse over something that "glows" (like icons, menu items, etc), the item will glow correctly on the mirrored monitor but it just doesn't show the pointer.

How can I fix this?

---

### Post by spegru on 2009-06-27
depends what version of ubuntu you are running.

If it's 8.10 then you can use the drivers from VIA, available here
[http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)
The vesa driver inside 8.10 works on the 2133 as long as you remember to pres f6 at boot time and add 'startxvesa' to the boot options but the VGA output doesn't work as well as no 3D effects.

If it's 9.04 on the other hand the although there is no need to startxvesa, the vesa driver still doesnt do the VGA port. There is no 9.04 driver availble from Via either so we are stuck unless anyone else has any bright ideas

spegru

---

### Post by j0nharris on 2010-01-20
9.04 drivers are available now, but of course, we've moved onto karmic... & no drivers for that yet!
> **spegru said:**
> depends what version of ubuntu you are running.

If it's 8.10 then you can use the drivers from VIA, available here
[http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)
The vesa driver inside 8.10 works on the 2133 as long as you remember to pres f6 at boot time and add 'startxvesa' to the boot options but the VGA output doesn't work as well as no 3D effects.

If it's 9.04 on the other hand the although there is no need to startxvesa, the vesa driver still doesnt do the VGA port. There is no 9.04 driver availble from Via either so we are stuck unless anyone else has any bright ideas

spegru

---

