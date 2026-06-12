---
title: "Poor streaming in ubuntu 10.4"
date: 2009-06-07
forum: General Help
---

### Post by Ceiber Boy on 2009-06-07
streaming online videos using Adobe flash 10, jitters and especially in full screen mode. this happens using BBC iplayer and youtube. 

i under have herd that this is a common problem, has anyone found a definite fix fir this problem?

using ubuntu 10.4

---

### Post by SeanTater on 2009-06-07
It happens to me all the time, but I know the reason. I got a real cheap-o video card and it doesn't play videos or anything really well. Usually you can improve the jitter by sizing down the video, so not quite so much of the screen has to refresh so often.

---

### Post by Ceiber Boy on 2009-06-07
So will increasing the screen refresh rate improve things?

---

### Post by Ceiber Boy on 2009-06-07
No! increasing the refresh rate dose not improve things! pity,

---

### Post by Ceiber Boy on 2009-06-07
.

---

### Post by fdm on 2009-07-30
temporarily reducing your desktop resolution to something closer to the resolution of the video you are trying to play will greatly reduce cpu load and poorly rendered video, especially when your on an older computer and are forced to use X11 instead of the hardware accelerated alternatives.

---

### Post by cottfcfan on 2009-07-30
You guys seem to have the same problem as me, ive mentioned this in several threads.
 Can u do me a favour, in you boot/grub/menu.lst, add acpi=off to your kernel line, update-grub, then reboot and let me know if the problem goes away and CPU usage is right down.
 You can easily reverse the change after.
 I`m sure this is a kernel/ACPI problem.

---

### Post by lisati on 2009-07-30
[COLOR="White"]Where can I get a copy of 10.4? I didn't know it was out yet......[/COLOR]

---

