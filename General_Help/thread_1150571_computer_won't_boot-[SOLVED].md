---
title: "computer won't boot-[SOLVED]"
date: 2009-05-06
forum: General Help
---

### Post by ewientje on 2009-05-06
Hi, my computer suddenly stopped booting.
I have one harddrive , one partition is Vista NTFS, the other is Ubuntu 9.04, ect3. It worked, until this morning, the computer couldn;t find a systemdisk, so I took the cd from Ubuntu, and via that cd I could access the grub,menu and start vista or ubuntu. Now I let Vista check his partition, and Vista says everything is fine, And Ubuntu says everything is fine at his end.
So, I think grub and all the partitions are working, why won;t it start from the harddrive? 
I thought the mbr bootrecord could be damaged, but recovery from the vista dvd, declared no errors found. I checked the bios, so it is still starting from the first harddrive, so does anyone over here have an idea ?
So there is nothing wrong, with the partitions, grubs or directory structure.But it won't boot.

---

### Post by x33a on 2009-05-06
what error are you getting?

does it go past the bios screen? check the cables, and if using sata, try changing the sata port.

---

### Post by geirha on 2009-05-06
Sounds like the BIOS has problems detecting the hard drive during boot. Does it list the hard drive if you enter the BIOS? Is it a desktop computer? If so, open the casing and check that the cable between the harddrive and the mother board is properly connected.

---

### Post by ewientje on 2009-05-06
It is a ide drive, desktop computer, and it is listed in the bios, if the connections were loose, would a live-cd still be able to start the grub from the harddrive ? Ubuntu is booting from the first harddrive, via the live-cd.
But I'll ask my husband to check the cable, I'll let you know if that could solve the problem. Thanks in advance.

---

### Post by dandnsmith on 2009-05-06
> **ewientje said:**
> It is a ide drive, desktop computer, and it is listed in the bios, if the connections were loose, would a live-cd still be able to start the grub from the harddrive ? Ubuntu is booting from the first harddrive, via the live-cd.

If Vista has checked things ...
then I can only think of 2 things

1) the HDD doesn't respond quickly enough - could be a disk starting to show it's age, or a PSU not delivering enough to start. This particular one will often declare itself - try restarting, without the CD in: if it then boots, you've found it.

2) the partition from which the system is trying to default doesn't have the 'active' flag set. Try the effect of ```
 sudo fdisk -l
```
from a terminal - one of the partitions should be flagged with an asterisk to tell the system code where to go.

---

### Post by frodon on 2009-05-06
As in post #2

What exact error message do you get ?

---

### Post by ewientje on 2009-05-06
Allright, thanks everyone for their help, the problem is solved, the bios went to the second harddrive, which isn't bootable, why it was changed to that I don't know, maybe because I had to diable network lan boot, and the bios arranged the order of booting itself. 
But both partitions now start up normally.
Thank you for reminding me to check the bios again, and for a third time, checking the bios i noticed.
How do I tag this as solved ?

---

### Post by frodon on 2009-05-06
> **ewientje said:**
> How do I tag this as solved ?I did it for you ;)

---

