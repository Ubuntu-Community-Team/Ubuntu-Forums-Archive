---
title: "EXT3 partition error - when accessing from Windows"
date: 2007-12-14
forum: Dell  Ubuntu Support
---

### Post by mushroomcloudwarrior on 2007-12-14
Hey,

I have an 80 gig EXT3 partition that i share between my Linux and Windows install.

For some reason, when i re-booted windows today, it doesn't let me access the partition. Instead i get the message "This disk is not formatted, Do you want to format it now?"

this is extremely scary as i have data i want on that drive..HELP!

---

### Post by elspiko on 2007-12-14
[http://www.fs-driver.org/download/Ext2IFS_1_10a.exe]("http://www.fs-driver.org/download/Ext2IFS_1_10a.exe")

Install that in Windows and it will give you full access to your EXT3 partition

---

### Post by mushroomcloudwarrior on 2007-12-14
i'm being a n00b and being stupid;

I just needed to shut Kubuntu down properly. Apparently, windows does that when the linux version is not shut down well..

Sorry!

---

### Post by sr20ve on 2007-12-14
> **mushroomcloudwarrior said:**
> i'm being a n00b and being stupid;

I just needed to shut Kubuntu down properly. Apparently, windows does that when the linux version is not shut down well..

Sorry!

That's because the disk was not properly unmounted.

I've seen something similar with my external hard drive when it wasn't properly unmounted.

---

