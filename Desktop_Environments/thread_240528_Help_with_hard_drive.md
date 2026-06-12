---
title: "Help with hard drive"
date: 2006-08-21
forum: Desktop Environments
---

### Post by fedeecheverri on 2006-08-21
I have two hard drives in my computer. I had windows in one of the drives,  the other one is formatted as NTFS, i just installed ubuntu in the one that had windows, now i want to format the other one as ext3 so i can read and write to it with ubuntu. How can I do this???? 

Thank you

---

### Post by stoeptegel on 2006-08-21
If you want to keep the data and have no other place to backup, you'll probably need partition magic(although i am not sure if it can do ntfs-> ext3 with keeping data). But then make sure you do a checkdisk and defragmentation from windows first. This can make the difference between having data on a converted filesystem or "having all the data lost".

If you can put it on a backup or you don't care loosing it, it's quite simple. Just make sure the drive is not mounted, fire up cfdisk, and start destroying and building partition(s).

---

