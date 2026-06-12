---
title: "extra entries in konqueror &quot;media:/&quot;"
date: 2008-01-24
forum: Desktop Environments
---

### Post by vibbizz on 2008-01-24
Hi all,

Having a bit of trouble with the "media:/" URL in Konqueror. It currently lists 6 partitions, some of which are duplicates. Entries in media:/ are:

10Gb Media    - /dev/hda1 mounted at /
10Gb Media    - /dev/hda6 not mounted
129Gb Media  - /dev/hda4 mounted at /home
48Gb Media    - /dev/hda9 not mounted
61Gb Media    - /dev/hda8 not mounted
61Gb Media    - /dev/hda2 not mounted

My hard drive only contains 3 partitions, 2 of which are mounted (the third is actually a Solaris 10 partition, and so not mountable) and a swap partition (which is on an extended drive). Output of fdisk -l /dev/hda:

/dev/hda1               1        1305    10482381   83  Linux
/dev/hda2   *        1306        8775    60002775   bf  Solaris
/dev/hda3           24544       24792     2000092+   5  Extended
/dev/hda4            8776       24543   126656460   83  Linux
/dev/hda5           24544       24792     2000061   82  Linux swap / Solaris

So where have /dev/hda6, 8 and 9 come from in the media:/ thing? They don't exist, they're not in fstab or mtab and I can't remove them.

Exactly the same thing happens in Xfce/Thunar.

Any help would be appreciated.

vibbizz.

---

