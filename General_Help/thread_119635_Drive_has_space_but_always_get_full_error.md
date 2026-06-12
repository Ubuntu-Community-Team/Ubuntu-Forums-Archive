---
title: "Drive has space but always get full error"
date: 2006-01-19
forum: General Help
---

### Post by Aikinai on 2006-01-19
Hi, I've recently installed Breezy and I love it, but I just noticed a pretty bad problem and I'm not sure if it's a bug. I have two hard drives and Ubuntu sees them and mounts them fine and under drives or system monitor it knows how much space they have overall and used. The problem is I can't add anything to the second hard drive (the OS is not on that one). I can delete things, and the drives/system monitor knows I've got more free space, but it still tells me destination is full if I try to do anything.
Here's everything I know so far:
-I added the hard drive after installation and I edited fstab to mount it (0 and 0 at the end of the line, do those affect it?). I don't think the fstab matters because even if I mount it manually under disks, I get the same problem.
-I changed the owner of all the files on the drive to my account
Here's the weird stuff...
-For some reason, if I sudo -s I can add files with no error. I know that makes it sound like I just don't have permission, but I do; it's definitely a drive full error in the gui and terminal.
-Here are the places that do and do not know it has space:
    System monitor knows the real total and taken space and knows there's stuff free
    Disks will always drop the total space to the amount taken so that it's full
    Properties of the folder I mount it to always says 0 free space

Thanks a lot for any help.

---

### Post by Aikinai on 2006-01-20
Well, it's working now. I just deleted some more stuff and now it says I do have some free space. I looks like there's just a discrepency in the overhead between the system monitor and the actual filesystem. I'm glad it's fixed, but I'd still appreciate if anyone knew what was going on and why root could write to the disk but my regular user couldn't.
Also, I just wanna say thanks for all the people that answer everyone's questions on this forum. I haven't posted before, but I've read a lot of other threads getting things set up.

---

### Post by qball on 2006-01-20
Linux, by default, reserves severall %'s of the filesystem.
Only root is able to write in this reserved space. (that's why it still works with sudo).

You can use tune2fs (the -m option I think, check the man page) to change the size of the reserved space.

---

