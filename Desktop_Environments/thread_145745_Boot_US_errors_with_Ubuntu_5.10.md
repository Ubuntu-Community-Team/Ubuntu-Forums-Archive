---
title: "Boot US errors with Ubuntu 5.10"
date: 2006-03-16
forum: Desktop Environments
---

### Post by Shyly on 2006-03-16
I just bought a new computer.  AMD64 3500, 1GB RAM, 128MB Nvidia Geforce 6600,  160GB WD HD(WinXP) and a 80GB Seagate HD(LInux).   I installed Ubuntu on the 80GB HD.   I partitioned the first 10GB as FAT32 and the next 20GB for Ubuntu.   The install went okay.  Everything was detected.  It ran good and I got it all updated.   

I use BOOT US as the boot manager to go between WinXP, Ubuntu, and PCLinuxOS on my last computer for several months and it worked fine with no errors and no problem.   However, after I installed Ubuntu on my new computer, Boot US showed errors that said W004: The partition does not start and end on the cylinder boundaries.   The partition was created with a partition manager which violates the established standards. You should use a partition manager which sticks to the established standards. This warning indicates a non-severe problem which can be ignored for the moment. 

It worked fine for 6 days.  Today, when I went to boot from the floppy into Linux, I got a red warning box that said something about a cylinder and that I couldn't boot.  So I tried to go back to Windows XP and now XP won't boot either.   Just a blank screen.   

If someone could explain to me why I got the error message from Boot US about the Ubuntu partition, maybe I can figure out why I can't boot into windows.   I'm trying to decide if all this is related to one thing or not.   

Thanks

---

### Post by PhoenixP3K on 2006-03-16
have you tested the hard disc drive on an other machine? I mean that cylinder thing and the fact that it "just stopped working" and that it's a new computer. The hard drive might just of died of a defect. I'm not familiar with Boot US (since I use GRUB). 

About Windows, it's far from being dual/multi-boot friendly, usualy you install it first then make the other OS work around it.

---

### Post by Shyly on 2006-03-16
WinXP is on the 160 GB HD and Ubuntu is on the 80GB HD.  There should not have been a problem between the two.   Even if the 80GB HD went out, it still should not have affected the other one unless there's a problem somewhere else.   

It's going back in to get checked out.  Thanks.

---

