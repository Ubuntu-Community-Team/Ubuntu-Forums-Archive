---
title: "star craft brood war"
date: 2005-12-14
forum: Gaming &amp; Leisure
---

### Post by linrasta on 2005-12-14
anyone had luck with getting brood war to run under wine?  It can't seem to find the cd when I go to start the game

---

### Post by nalmeth on 2005-12-15
wine might not have set up the cdrom when you installed it. This is exactly the same problem I had with Starcraft (original)

simply open a terminal and type:
winecfg

go to drives, and add a new device
call it /cdrom/
and select the device type cdrom
just auto-detect the serial number part

now as long as the drive is mounted, it should work!

good luck to ya

---

### Post by rado_london on 2006-01-17
I did it and it works perfectly.
I recorded that Starcraft runs a bit slow under wine. Probably someting is wrong with the configuration. Are there any tricks about wine conffig and Starcraft.

Thanks in advance!

---

