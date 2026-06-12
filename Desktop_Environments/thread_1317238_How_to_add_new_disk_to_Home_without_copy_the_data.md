---
title: "How to add new disk to Home without copy the data"
date: 2009-11-06
forum: Desktop Environments
---

### Post by mobee on 2009-11-06
I have an Ubuntu machine with 160GB hard drive.
I have notice that my disk space is on the limit though I have 100BG for Home folder in *separated partition*.
I would like to purchase a new disk and connect it as second disk on the same computer, but I also like to have the new disk space combined with my Home partition as is now.
In other words I would like Ubuntu to take the additional disk space and use it to extend to my Home directory so I will have 100GB + 500GB(of the new disk) for my available to my Home folder.
Something like mounting multiple partitions to become same mount point (/home/user) I guess that it is more complex then just mounting a partition to a logical name, it mast involve the kernel somehow.
Any idea?
Is there any solution I can use, a work around?

I found [that link]("http://linux.die.net/man/2/mount") says that "Since Linux 2.4 a single file-system can be visible at multiple mount points, and multiple mounts can be stacked on the same mount point."

I will keep searching for solution... if someone managed to do that I'll be glad getting some help.

10x,
Moshe Beeri.

---

### Post by mobee on 2009-11-06
This [link]("http://lkml.indiana.edu/hypermail/linux/kernel/0102.0/0957.html") claims it works, though I have not tried it yet

---

### Post by Jive Turkey on 2009-11-06
The simplest method would be to create an empty folder in your home directory and set /etc/fstab to mount the new drive there. This works for sure. Any files written to the new folder would be on the new disk.  You could still run out of space on the rest of your /home directory however.  If you have a particular use that consumes a lot of your disk space (for me its videos and music) I would mount the drive to use those folders, and move/copy my stuff into it later.  IME linux does not like to mount drives to non empty folders.  Alternatively, you could mount it as a new folder in /newdrive, chown it copy your data to it and make symlinks in your home folder pointing to the directories on the newdrive.  Come to think of it, there are probably lots of other ways to approach this.

The method mentioned above sounds interesting but I would not be at all surprised if you ran into major problems with it.

---

### Post by mobee on 2009-12-18
Hi Jive,
I did run into few problems with the method, and I just abundant that, in some way it seems not logical one can not add more and more disks to increase disk space while keeping it transparent to the home user.
I have installed Fedora recently and discovered the LVM (Logical Volume Manager) That I think will be supported from 10.04 on, it so close to what is needed, the only think left to do is to create a dynamically growth LVM.
I really really hope that the guys that wrote LVM will go a bit further to develop a dynamic version.
Of course I agree with you, today's best method is to mount a partition or disk to a folder to be used to store a certain type of data.

---

