---
title: "help mounting drives"
date: 2009-02-25
forum: General Help
---

### Post by antonyant11 on 2009-02-25
i recently installd kubuntu on my pc...it seems to be working fine but i have an issue reading drives.  Pretty sure I just have to mount them but im not sure how

ant@conan-the-destroyer:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf28af28a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       38912   281844360    f  W95 Ext'd (LBA)
/dev/sda5            7650       38912   251120016    7  HPFS/NTFS
/dev/sda6            3825        7486    29414952   83  Linux
/dev/sda7            7487        7649     1309266   82  Linux swap / Solaris

Partition table entries are not in disk order
ant@conan-the-destroyer:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda6              28G  3.1G   24G  12% /
tmpfs                 3.0G     0  3.0G   0% /lib/init/rw
varrun                3.0G  100K  3.0G   1% /var/run
varlock               3.0G     0  3.0G   0% /var/lock
udev                  3.0G  2.8M  3.0G   1% /dev
tmpfs                 3.0G     0  3.0G   0% /dev/shm
lrm                   3.0G  2.4M  3.0G   1% /lib/modules/2.6.27-7-generic/volatile
ant@conan-the-destroyer:~$


not really sure what I should be doing here but im pretty sure im on the right track

---

### Post by nelskurian on 2009-02-25
Do you have issue when accessing the NTFS partitions.For accessing NTFS partitions you have to install NTFS3G package.needs more clarity..

---

### Post by antonyant11 on 2009-02-25
ntfs-3g is installed

the problem is I cant acces the ntfs drives through dolphin. I click on them but the slected item just reverts to root or home.

i was wondering .. maba a permission problem..?

---

