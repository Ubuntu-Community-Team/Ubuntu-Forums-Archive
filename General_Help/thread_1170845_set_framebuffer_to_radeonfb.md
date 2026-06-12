---
title: "set framebuffer to radeonfb?"
date: 2009-05-26
forum: General Help
---

### Post by dpsleep on 2009-05-26
I'm trying to get my laptop to use the radeonfb at startup so i can have 1280x800 but i cant seem to get it to load. I've tried adding it to /etc/modules, I've tried adding video=radeonfb to my kernel line, and I've tried adding radeonfb to my /etc/initramfs-tools/modules file and updating the initramfs. but it still wont use it, "cat /proc/fb" gives me 0 VESA VGA. im using the open source radeon driver in 9.04 and my video device is:

01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]


anyone have a clue as to what I'm doing wrong?

---

### Post by dpsleep on 2009-05-26
bump...

---

### Post by L_V on 2009-07-04
You should read this: [_Gutsy Framebuffer_](http://ubuntuforums.org/showthread.php?t=652038)

---

