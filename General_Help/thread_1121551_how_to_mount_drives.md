---
title: "how to mount drives ??"
date: 2009-04-10
forum: General Help
---

### Post by chinmaya_n on 2009-04-10
I would like to know how to mount drives to /media from the terminal using some commands..... or can we have any possibility to mount drives to any other location. can any one help me. plzz

Thanks in advance:popcorn:

---

### Post by Thura on 2009-04-10
[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

---

### Post by ameermawia on 2009-04-10
for mounting any drive you have to type the following command:
sudo mount -t filesystemtype /dev/sdax /media/disk

here filesystemtype is the file system you are having on the drive which  you want to mount.all the drive which you have is present in /dev .in sdax
x stands for any no. 1,2....6,7..which you can find out from the dev directory.

ex. mount -t vfat /dev/sda1 /media/disk
also you have first make directory disk in media by using the command
sudo mkdir /media/disk

---

### Post by ameermawia on 2009-04-10
yeah i forget to mention that you can mount the drive at any location you desire.
mount works like
mount -t type something somewhere
so in the command of previous post just replace /media/disk to any desire location like /home/newfolder

---

