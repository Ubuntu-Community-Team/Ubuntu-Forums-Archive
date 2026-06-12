---
title: "Cannot Install Update on Hardy"
date: 2009-04-27
forum: General Help
---

### Post by knife_party on 2009-04-27
Hi there everyone,

I have this problem that I cannot install any upgrade by using Synaptic. Everytime I want to install after the file has already downloaded, i always get a message like this:

E: /var/cache/apt/archives/libc6-i386_2.7-10ubuntu4_amd64.deb: failed in buffer_write(fd) (10, ret=-1)

And this occur to many different software that i try to upgrade. Previously, i have managed to use synaptic succesfully to install many softwares, but why I can't do it again this time? ANy help everybody?

Thank you very much

---

### Post by knife_party on 2009-04-27
And o yeah, after running df-h, i get these message:

> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             9.7G  6.7G  2.6G  73% /
varrun                502M  100K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M   96K  502M   1% /dev
devshm                502M  148K  502M   1% /dev/shm
lrm                   502M   43M  460M   9% /lib/modules/2.6.24-16-generic/volatile
/dev/sda9             2.9G  2.9G     0 100% /usr
gvfs-fuse-daemon      9.7G  6.7G  2.6G  73% /root/.gvfs
/dev/scd0             219M  219M     0 100% /media/cdrom0
/dev/sdb5              38G   37G  332M 100% /media/Didzilla
/dev/sdb6              38G   37G  392M  99% /media/sonicfest
/dev/sdb1              38G   36G  1.7G  96% /media/KillDit


So i guess probably the diskspace is not a problem

---

### Post by DagMan on 2009-04-27
do **df -h** and see if you have any full partitions.  That could be the cause of it.

---

### Post by knife_party on 2009-04-28
you can see from the output, the /dev/sda6 is the only partition i used for Ubuntu, and it's only 73% used, is it not enough?

---

### Post by JKyleOKC on 2009-04-28
> **knife_party said:**
> you can see from the output, the /dev/sda6 is the only partition i used for Ubuntu, and it's only 73% used, is it not enough?

It shows that /dev/sda9 is full, and indicates that's where you have mounted /usr. Since most all updates involve writing code to /usr/bin, this may be your problem...

But if sda9 is for some other distribution, it's probably not...

---

### Post by knife_party on 2009-04-29
ooo, okay, i see...hmm probably gonna fix it tonight, thank you JKyleOKC :D

---

