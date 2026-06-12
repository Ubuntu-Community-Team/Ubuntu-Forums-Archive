---
title: "GRUB is gone? o_O"
date: 2006-08-29
forum: Desktop Environments
---

### Post by nahtical on 2006-08-29
OK......this should be the right place to ask. I've been dual booting Dapper and Windows XP on this laptop, and it was working great. Problem is one day when I got home, I started it up and it went straight into XP, with no GRUB options. I have installed a driver for XP to read Ext2/3 partitions, and all my data from Linux seems intact, but GRUB seems to have gone away. I suspect the power went out sometime during the day and drained the battery to 0, since if I recall correctly it was totally drained when I started it up, and I know it likes to do funny things when it drains the battery, like totally track of time (would a laptop have a CMOS battery[or whatever that little watch battery on motherboards is called]?). Like I said, it looks like the data is there, just no GRUB, or at least GRUB isnt wanting to start.

---

### Post by Ramses de Norre on 2006-08-29
Boot up a live disc and do this in terminal:
```
sudo grub
root (hd0,0)
setup (hd0)
quit
sudo update-grub
```

This will install grub to the MBR (the hd0 part) and will look for a menu.lst on hda1 (the hd0,0 part, grub uses only numbers and starts counting from 0).
Change this values to your needs/likings.

---

