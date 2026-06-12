---
title: "How to auto mount FAT32 volume at startup?"
date: 2007-05-20
forum: Desktop Environments
---

### Post by almightybunghole on 2007-05-20
Hi folks,

I'm running Ubuntu Feisty on my nx9420 laptop and it's working very well :p. I'm in the process of snagging the little bits and pieces now that most things are working as expected!

I would like to mount my FAT32 data volume at startup - at the moment I navigate to it using Nautilus and enter my password before getting access to data on the drive. How can I do this automatically so the volume is available when Ubuntu starts?

Thanks.

George

---

### Post by andrea54 on 2007-05-20
that's pretty easy :-) start the terminal (or konsole) and start gparted. there find the name of your fat32 partition (for instance /dev/sda1). then, in the terminal, do the following: 

sudo kate /etc/fstab

there add a new line that looks like this: 

DEVICENAME        MOUNTPLACE   vfat      defaults     0       0

for instance when you want that volume to be mounted in /media/fatdrive and it's called /dev/sda1 the line would read

/dev/sda1        /media/fatdrive   vfat defaults     0       0

then close kate, and create the place where it will be mounted (in the terminal, write:)

sudo mkdir /media/fatdrive

or whatever you called it ... and tada the next time you boot it will be mounted automatically. you can of course mount it right away with a simple

sudo mount -a


that's all....

---

### Post by mtbsoft on 2007-07-08
Thanks andrea54, you solved my problems.

---

