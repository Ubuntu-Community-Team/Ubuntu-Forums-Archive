---
title: "Removing Primary Hard Disk - How Do I Reconfigure Grub"
date: 2009-05-05
forum: General Help
---

### Post by ajacx on 2009-05-05
I've got a dual boot desktop and two hard disks, one has XP and the other has Ubuntu. XP is primary. From what I've heard, grub is usually installed on the first sector of the primary's hard disk, correct? Now it looks as though the XP hard disk is going to conk out, so I'd like to remove it and use the Ubuntu as primary. I assume that I need to reconfigure Grub to only recognize one hard disk and set it up to boot from the Ubuntu hard disk? I've looked around but haven't been able to find out how to do this, can you please tell me if my assumptions so far are correct and how to go about solving this?

Thanks

---

### Post by kay-man on 2009-05-05
You'll need to both reconfigure and reinstall grub because it is normally installed to the master boot record (MBR) of the first hard drive, which will be a different one.

Basically, what you need to do is tell grub where it can find a root partition, i.e. one that has an OS that your PC can boot from. This is the GRUB root command. The setup command then writes the information to the disk. Finally, this infor needs to be in line with what's written in your GRUB menu.lst file.

I've had a similar situation on my hands recently, and [this thread]("http://ubuntuforums.org/showthread.php?t=224351") has been very helpful.

Before you start, make sure you have a live CD at hand in case anything goes wrong.

---

### Post by ajacx on 2009-05-05
Thanks paulklos, for explaining the process and also for the thread link, I think I understand what to do now. As luck would have it, a few minutes after posting this thread, I came across [this solution here]("http://ubuntuforums.org/archive/index.php/t-912254.html"), which pretty much says the same thing. Unfortunately I've only been using alternates to upgrade and have a very old live CD, but it looks like it should be fine without one. Much appreciated!

---

