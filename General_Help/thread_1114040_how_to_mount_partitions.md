---
title: "how to mount partitions"
date: 2009-04-02
forum: General Help
---

### Post by shivam89 on 2009-04-02
i m new to linux and i m not able to mount my disk partitions.
somebody explain the procedure for mounting partitions. i had try doing it using mount command but it tells to look up into **_/etc/fstab_** where i could not find anything regarding my partions. i was able to mount CD from there but not the disk.
do i hav to edit **_/etc/fstab_**

---

### Post by xenophed on 2009-04-02
well the long and short
shortest
look under [places on menu next to applications] for the partition
short
open xterm
sudo mount /dev/(device name) /mnt/(mount point)
long 
sudo edit /etc/fstab
note all lines with a # at the beginning are disabled remove #
in xterm type man fstab

---

### Post by tjwoosta on 2009-04-02
yea fstab is where you setup partitions to be automounted on boot


if you only want to mount it once you should be able to just use the mount command like described above

---

### Post by nebileix on 2009-04-02
try here [http://ubuntuforums.org/showthread.php?t=972559&page=1]("http://ubuntuforums.org/showthread.php?t=972559&page=1")

---

### Post by oldos2er on 2009-04-02
[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

---

