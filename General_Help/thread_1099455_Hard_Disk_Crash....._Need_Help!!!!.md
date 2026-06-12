---
title: "Hard Disk Crash..... Need Help!!!!"
date: 2009-03-18
forum: General Help
---

### Post by nebu on 2009-03-18
My hard disk partition that has Ubuntu installed has crashed..... so my grub is not able to load .... it gives me error 17......

i also have windows vista installed on one of my partitions..... how do i restore the windows bootloader or make grub boot into windows dirctly

---

### Post by jwbrase on 2009-03-18
> **nebu said:**
> My hard disk partition that has Ubuntu installed has crashed..... so my grub is not able to load .... it gives me error 17......

i also have windows vista installed on one of my partitions..... how do i restore the windows bootloader or make grub boot into windows dirctly

Let me make sure I've got this right:

You have Windows and Ubuntu installed to two partitions on the same disk.

Ubuntu was loading, and now it isn't, and you didn't make any changes to GRUB's menu.lst file.

You have reason to suspect a hard drive crash (such as the drive making strange clicking noises), as opposed to something like data corruption (which might be caused by not having shut the machine down cleanly). 

If you've actually had a hard drive crash, then it's not limited to one partition. The whole disk is dead. If Windows is on another partition on the same disk, it's very likely that it won't boot either.

---

### Post by cariboo on 2009-03-18
In a case like yours, I would go to the hard drives manufacturers web site and download the diagnostic tools for your hard drive and run them, to be sure if it actually is the hard drive that has gone defective.

If the drive passes all the tests, have a look at this [thread=224351]page[/thread] to repair grub.

Jim

---

