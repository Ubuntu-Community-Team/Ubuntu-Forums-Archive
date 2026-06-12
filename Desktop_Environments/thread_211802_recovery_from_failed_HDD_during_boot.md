---
title: "recovery from failed HDD during boot"
date: 2006-07-08
forum: Desktop Environments
---

### Post by plm99 on 2006-07-08
This isn't so much a bug complaint as it is a suggestion.

I am running the latest Dapper Drake install, and I have been very happy with the Ubuntu distro for quite a long time now.

My system, like I'm sure many other people, has evolved to it's current state over many years, and consequently has 4 hdd at this time. I know, I should do some housekeeping, but... Occasionally, one of the older drives doesn't initialize properly, (not one with the OS on it), but it causes the OS boot to hang indefinately.

I know I can solve this by either
a.) Hard reset the mother board until the offending hdd complies
b.) Edit fstab and not mount the drive

BUT, it would be nice if there was a way for the boot script to detect that the drive has a problem (maybe it times out?) and either skip over it or at least ask the user if it should ignore the drive.

What do you think, is this feasible?

---

