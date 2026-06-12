---
title: "Fsck gets stuck on reboot"
date: 2009-03-07
forum: General Help
---

### Post by bigred1 on 2009-03-07
My Ubuntu required a file system check on reboot. I use AutoFsck, and after shutdown and reboot I let it run.

It has now been seven hours and the reboot is stuck -- no changes in what appears on the screen.

The last lines are 

```
fsck 1.40.9 (1-Mar 2008)
Checking drive /dev/sdb1: 0% (stage 1/5, 1/1147)
/dev/sdb1: 662546/18792448 files (2.0% non-contiguous), 24247511/37561970 blocks 
```

What do I do? If I just hard-reboot I will be required to run fsck again. 

Is there a way to bypass and reset this?

My Ubuntu is fully updated, and is running on an commodity Intel chipset, with a 120 GB disk.

---

### Post by dcstar on 2009-03-07
> **bigred1 said:**
> My Ubuntu required a file system check on reboot. I use AutoFsck, and after shutdown and reboot I let it run.

It has now been two and a half hours and the reboot is stuck -- no changes in what appears on the screen.

The last lines are 

```
fsck 1.40.9 (1-Mar 2008)
Checking drive /dev/sdb1: 0% (stage 1/5, 1/1147)
/dev/sdb1: 662546/18792448 files (2.0% non-contiguous), **24247511**/37561970 blocks 
```

What do I do? If I just hard-reboot I will be required to run fsck again. 

Is there a way to bypass and reset this?


You can stop auto-fsck for a partition by changing the last value in the /etc/fstab entry to 0.

---

### Post by bigred1 on 2009-03-08
The solution was to reboot in recovery mode. The fsck ran in the usual  amount of  time. I was then able to reboot properly. So, something in the regular boot froze fsck, even though fsck runs near the beginning  of the boot sequence.

The freeze occurred in several attempts to reboot regularly, so it was not a one-off problem.

I still do not know what the problem was.

Strange, and worrisome. The fsck-freeze problem (and I was even using AutoFsck) makes me feel that my computer is permanently lost. 

This never happens in Windows. And in 15 years of using Windows, I've never lost a computer to a OS-corrupted file-system..

---

### Post by dcstar on 2009-03-08
> **bigred1 said:**
> The solution was to reboot in recovery mode. The fsck ran in the usual  amount of  time. I was then able to reboot properly. So, something in the regular boot froze fsck, even though fsck runs near the beginning  of the boot sequence.

The freeze occurred in several attempts to reboot regularly, so it was not a one-off problem.

I still do not know what the problem was.

Strange, and worrisome. The fsck-freeze problem (and I was even using AutoFsck) makes me feel that my computer is permanently lost. 

This never happens in Windows. And in 15 years of using Windows, I've never lost a computer to a OS-corrupted file-system..

Either your Ubuntu system is gone or it isn't, which is it?

If is is still there then you haven't "lost" anything so I don't know what the problem is.

---

