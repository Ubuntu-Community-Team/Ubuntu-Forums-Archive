---
title: "Issues with nvidia proprietary drivers"
date: 2010-08-12
forum: Desktop Environments
---

### Post by pipemartinm on 2010-08-12
Bit of a newbie question, so apologies in advance.
 I've just built myself a media PC using ubuntu 10.04 and XBMC.  XBMC   requires hardware acceleration so I installed the Nvidia proprietary   drivers. They don't however seem to be able to detect my plasma and only   give me the 4:3 resolution options. There doesn't seem to be an option   in the GUI front end to force it to enable them (similar to unticking   the 'only display resolutions my display can handle' box in XP) is  there  a way to enable the other resolutions in the X windows or nvidia  config  files?

---

### Post by pipemartinm on 2010-08-12
Bump. Does anyone know if the Nouveau drivers are any better?

---

### Post by Wisp558 on 2010-08-12
I for one dislike nouveau, and for a performance home theatre machine, it would be suboptimal, I think. It's still rather buggy and under heavy development.

You can try nvidia-xconfig (just pop that into the terminal), as it's nvidia's gui.

You can also try this: [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

's prolly your best bet.
You could also try looking up xrandr, I don'r recall whether it does resolutions or not.

Good Luck.

---

