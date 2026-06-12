---
title: "Input/Output Error"
date: 2006-07-10
forum: Desktop Environments
---

### Post by jmhickman09 on 2006-07-10
A couple months ago I installed 5.04 on my Dell to dual-boot with XP Home. So now I'm installing 5.10 on my friend's PC over top of XP. During partitioning, I always get an error (even after trying different formats and sizes.) So here it is:

**input/output error during read on /dev/ide/host0/bus0/target1/lun0/disc ERROR!!**

Then I say ignore, and it comes up again, and I hit ignore, and then it fails to write the new partitions. Is this a hardware error? I don't think it is, because Windows was working fine before. I just found out ubuntu 6 is out, but I already had 5.10 on a cd. Thanks for your help.

---

### Post by jmhickman09 on 2006-07-10
bump

---

### Post by Sonofmoog on 2006-07-10
I'm not sure I know what you mean by *over top of XP, *but that is likely your problem.  My recommendation is to start again.  You can zero out the disk with

```
cat /dev/zero >> /dev/hda 
```

Recommend you do so, then fireup the LiveCD and try to partition .. 

Another option might be to load the Windows CD like you're going to install Windows, let it partition the drive if it can, then install Ubuntu ..

---

