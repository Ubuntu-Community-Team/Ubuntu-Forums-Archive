---
title: "Ubuntu 8.04 on Dell PE1950 with MD1000 on second RAID controller not working."
date: 2008-11-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by UPCO on 2008-11-18
Howdy,

So I have a Dell 1950 with two internal HDDs on a PERC6/i controller as well as an MD1000 (RAID10) on a PERC6/E controller.  The internal drives work fine.  The RAID on the MD1000 is not recognized by the system.  cat /proc/partitions looks like:


```

cat /proc/partitions 
major minor  #blocks  name

   8     0  142737408 sda
   8     1  136897866 sda1
   8     2          1 sda2
   8     5    5831563 sda5

```


I've installed megaraid_sas drivers as instructed here:

[http://ubuntuforums.org/showthread.php?t=719556&page=3]("http://ubuntuforums.org/showthread.php?t=719556&page=3") 

with no luck.  Has anyone ever encountered this before?

---

### Post by UPCO on 2008-11-19
So I think I've boiled the problem down to the fact that no virtual disk is configured on the array.

So, I went ahead and got OMSA working on the box, logged into the interface and everything looks functional.  All the disks are listed, etc.  So, when I go to the "Create virtual disk wizard", I get "Insufficient Priviliges to perform the action!".  I can view any other page in the interface and make changes to any other settings.  Just cant seem to employ this task.

So this leads to 2 questions:

1. Has anyone encountered this before and discovered a fix?

2. Is there a method for configuring the vdisk from the CLI?


Thanks.

---

### Post by UPCO on 2008-11-19
I figured it out.  Just did this:

```

omconfig storage controller action=createvdisk controller=1 raid=r10
size=max pdisk=0:0:0,0:0:1,0:0:2,0:0:3,0:0:4,0:0:5

```

and all is well.

---

