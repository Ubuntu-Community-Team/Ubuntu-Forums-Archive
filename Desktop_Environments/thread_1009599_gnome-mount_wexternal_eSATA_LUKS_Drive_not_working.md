---
title: "gnome-mount w/external eSATA LUKS Drive not working"
date: 2008-12-12
forum: Desktop Environments
---

### Post by wootah on 2008-12-12
[SIZE=4]Hey folks![/SIZE]

[SIZE=2]Situation[/SIZE]
I have an 500GB Seagate in an external drive enclosure with an eSATA interface. This drive has two partitions, one ~470 encrypted LUKS partition (with ext3) and the rest to another partition w/NTFS.

[SIZE=2]Problem[/SIZE]
For whatever reason, when I connect the drive to my laptop through the eSATA interface to the external drive, gnome-mount does not start; BUT, there is information displayed in dmesg about the connection being established.

After I plug in the drive, I can call "*gksudo* *gnome-mount -vbd /dev/sdb1*" and it will prompt me for a LUKS password as expected, and mount the drive to /media/disk.

[SIZE=2]Questions[/SIZE]

[LIST=1]
[*]Why does gnome-mount not launch when I plug in the hard-drive ?
[*]How can I specify where to mount the drive if after gnome-mount is successful ?
[*]Is there a better way to do this ? (I actually wanted to specify in /etc/fstab and /etc/crypttab about my external, but I might not always have the drive connected when I turn on my laptop, thus it would fail and drop down to root shell where I can continue.)
[/LIST]
Thanks very much guys!
~Jaymes

---

### Post by wootah on 2008-12-12
Perhaps related to: [https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/193961](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/193961)

---

### Post by wootah on 2008-12-20
Bump.

Additional information: The drive also has a USB interface--connecting by USB brings up gnome-mount.

---

### Post by kagou on 2009-03-20
Have a look at :
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/153768](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/153768)

---

