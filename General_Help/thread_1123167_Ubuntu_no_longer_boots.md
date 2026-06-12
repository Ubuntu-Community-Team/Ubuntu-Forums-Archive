---
title: "Ubuntu no longer boots"
date: 2009-04-11
forum: General Help
---

### Post by jim6893 on 2009-04-11
I installed Ubuntu into my data drive about a month ago using windows, I became fed up with Windows and formated the C: Partition which had windows in it and now I no longer have a boot option for Ubuntu.
The installation was done in windows but it was installed into the D: drive.

---

### Post by defaultusername on 2009-04-11
jim6893,

Did you happen to wipe the MBR? Are you using GRUB or LILO? Post an example of the partition table.

---

### Post by jim6893 on 2009-04-13
I have two partitions of 70gb each, C: & D:
C: had windows and I installed Ubuntu 8.10 using windows into D:
I have formatted C: and reinstalled Vista but the menu that came with Ubuntu does not load. I downloaded Super Grub disk but i am unable to find the Ubuntu OS off my D drive. I am asuming I deleted the mrb when I formatted C drive

---

### Post by Agent.Logic_ on 2009-04-13
It is kind of tedious to migrate to a wubi install and wipe out Windows completely, but its nothing that can't be done. Check out [this article](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?), probably what you are looking for. Hope it works for you, good luck!

---

