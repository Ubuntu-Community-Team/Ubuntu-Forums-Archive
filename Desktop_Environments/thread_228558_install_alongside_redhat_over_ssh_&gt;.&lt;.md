---
title: "install alongside redhat over ssh &gt;.&lt;"
date: 2006-08-03
forum: Desktop Environments
---

### Post by redbull_monsta on 2006-08-03
ok so here is the deal

i have a fedora core 5 system running 200 miles away and i need to do some testing with ubuntu on it.... there are specific reasons i have to use this box that really dont need explaining, Anyway i need to install the ubuntu environment allongside FC5. then reboot into ubuntu.

heres the problem

1) the box is 5 hours drive away
2) i only have ssh/ftp access to the box at the mo
3) i need to get ubuntu installed asap

the HD is only 10gig and looks like this

[root@linuxbox ~]# df -h
Filesystem            			Size  Used Avail Use% Mounted on
/dev/mapper/VolGroup00-LogVol00		8.1G  4.1G  3.7G  53% /
/dev/hda1              			99M   14M   80M  15% /boot
tmpfs                 			248M     0  248M   0% /dev/shm

now i was hoping i could extract the basic filesystem onto the box, chroot accross and configure the basics like networking and ssh and ftp, then delete the FC5 install, but how do i get the system to reboot and be sure i get ubuntu running.

any help would be great

---

### Post by redbull_monsta on 2006-08-05
I done the drive :(

---

