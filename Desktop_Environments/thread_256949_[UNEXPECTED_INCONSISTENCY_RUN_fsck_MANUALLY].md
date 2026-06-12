---
title: "[UNEXPECTED INCONSISTENCY: RUN fsck MANUALLY]"
date: 2006-09-13
forum: Desktop Environments
---

### Post by jigantor on 2006-09-13
Trying to boot my desktop this morning it forced a check (30 mounts), but instead of going through happily like usual gave me this message:

```
UNEXPECTED INCONSISTENCY: RUN fsck MANUALLY

An automatic file system check of the root system failed.
A manual fsck must be performed, then the system rebooted.
This fsck can be performed in maintenace mode
Please note that the root file system is currently mounted read-only.
The fsck should only be performed while the root filesystem is mounted read-only[
...]

```
I've never used fsck before and I'm not quite comfortable with the command line yet. What command should I use at this point?

---

### Post by piroshki on 2006-09-14
I think the syntax is just:
```
fsck /dev/partition
```
You will need to replace /dev/partition with the device name of your root partition. If you don't already know what it is, the following command should give you the name to use (on the left hand side on the ouput):
```
mount | grep ' on / '
```
It's probably going to be something like /dev/hda1 or /dev/sda1.

Before you do this, you currently have the filesystem mounted read-only, now would be an excellent time to back-up anything you don't want to lose to another partition or wherever you can manage in case you have to attempt a repair. If you have trouble backing up, you may want to get hold of a Knoppix rescue disk [http://www.knoppix.net/](http://www.knoppix.net/).

---

### Post by jimmccool on 2008-04-26
Thanks! This really saved my skin. I'll know what to do now when this happens again.

Is it a good idea to use "fsck -y /dev/your-affected-partition' ? so you dodn't have to keep pressing y?

In any case a BIG THANKS to everybody who helps on these forums.

---

