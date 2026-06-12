---
title: "Random segmentation fault"
date: 2006-09-13
forum: Desktop Environments
---

### Post by swamytk on 2006-09-13
I have Dapper 6.06.1. After installation I restarted observed the following:
1. Firefox runs fine as root user. But as my normal user, it silently exit without even opening window. I launched it from shell prompt also, it does not throw any message other than usual local modifier warning.
2. Evolution throws segmentation fault.
In the same PC, Dapper 6.06. was running with some random exit of application in rare occassion.

I suspect bad block in file system. So I am running "sudo e2fsck -pccfv /dev/hda2" on my root and home partitions. Is it enough or any other reason for this?

---

### Post by lagagnon on 2006-09-13
I suspect a hardware fault: your hard disk is dying or one of your memory sticks is faulty. Try the fsck, if no joy then try "smartctl" (read man smartctl). If that does not tell you something download your hard drive manufacturer's diagnostic diskette and test your hard drive. Lastly, run memtest from the Ubuntu CD.

---

### Post by Shay Stephens on 2006-09-13
I am having the same problem.  Firefox quits unexpectedly, and so does thunderbird, and epiphany.  Firefox gives the segmentation fault error.  And as hinted at above, I believe it is a hardware problem.  

I need to replace my motherboard or ram, not sure which, but I am going to do both when I get a dual core processor.  I dual boot with windows, and windows has trouble too.  So when I installed ubuntu and it started acting unstable I knew what the problem was.

---

