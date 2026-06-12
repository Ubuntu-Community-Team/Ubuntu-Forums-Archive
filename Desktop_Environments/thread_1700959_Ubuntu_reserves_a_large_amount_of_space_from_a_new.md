---
title: "Ubuntu reserves a large amount of space from a new partition"
date: 2011-03-05
forum: Desktop Environments
---

### Post by runyonave on 2011-03-05
In gparted I have the following stats for my /home drive

size: 824 gb
used 75.51 gb
unused 748.59 gb


Now when I view this in nautilus it shows something else: remaining free space as 709 gb. My question is what happened to the 40gbs? the 75.51gb are my files, but where did the 40gbs go to?

Because  709 (total remaining) + 75 (my files) + 40 (mysteriously lost gbs) = 824gb.

When I first made the partiton, it was a 824gb partition and ubuntu had automatically at that point reserved about 40gb for something. Does anyone know why Ubuntu reserved this space?

Thanks.

---

### Post by asmoore82 on 2011-03-05
A certain percentage of free space is reserved by default for system
and/or superuser use only. The idea is that this space is a buffer zone
that prevents users from creating a massive zero free space condition,
either accidentally or maliciously, that crashes the system.

The percentage is OK for small drives but obnoxiously large for huge drives.

For non-OS partitions of user data, I believe it is 100% safe to turn this off.

To check the current reserved space: ```
sudo tune2fs -l /dev/sda1 | grep -i reserve
```
To change it by percentage: ```
sudo tune2fs -m 0 /dev/sda1
```
^In both cases, you may need to change "/dev/sda1" to suit your system layout.

---

### Post by runyonave on 2011-03-05
Hey asmoore82 thanks a lot for the reply. Now I understand what the reserved space is for. BTW I have about 100gb stored for the /root partition. I accidentally removed the reserve space limit on it. Is a 100GB (now 93gb) space enough for /root or should I add some reserve space to it? Thanks again.

---

### Post by asmoore82 on 2011-03-05
I'm not sure what you mean by "/root partition" but I'm assuming you mean
the top level root partition of no name: "/" There is a "/root" folder that
is the root user's personal home directory which is typically empty.

For the "/" root partition itself, it's interesting that you should ask,
because
I have a 12GB partition for mine and only 78MB is currently free! :lol:

I would now recommend at least 16~20GB.

---

### Post by runyonave on 2011-03-05
Thanks, I guess mines has enough space.

---

