---
title: "Problem Installing Ubuntu- File System Mount Error"
date: 2006-08-08
forum: Desktop Environments
---

### Post by thistlebrae on 2006-08-08
Hello all,

Will keep it brief.  I am attempting to install 6.06 LTS.  The GUI install program gets to the second step (titled something like mounting primary file system) but then hangs.

I think the problem is that the drive is new and not formatted.  Is there not a formatting capability in the Ubuntu installer for a virgin drive.  If I had an operating OS on the drive I probably wouldn't be installing Linux on the drive.  Can anyone help?  Is there a minimum formatting option I can use and how can I do that?  Would I have to mount it externally and then use something like Partition Magic.  Does it have to be formatted as a bootable drive?

Any help would be most appreciated.

Thanks,
Todd

---

### Post by coffeecat on 2006-08-08
I really don't know whether an unformatted drive is the problem but, yes, there is a partition utility on the Ubuntu Dapper live CD. After you've booted up with the CD, go to System > Administration > Gnome Partition Editor (that's Gparted) and partition away!

On second thoughts the unformatted disk might be your problem and it might be needing a volume name. Gparted will do that for you. Post back if you need any help choosing partition sizes, filesystems, etc.

---

