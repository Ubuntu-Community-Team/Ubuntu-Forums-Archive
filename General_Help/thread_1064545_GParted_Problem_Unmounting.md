---
title: "GParted Problem Unmounting"
date: 2009-02-08
forum: General Help
---

### Post by leenyx64 on 2009-02-08
Hello everyone,

I have a problem regarding repartioning my HDD.  I have a 250GB HDD running 64bit Ubuntu 8.10.  I want to repartion the HDD to dual boot Windows 7 and also have a shared partion for media.  I am doing this so i can run itunes on the windows partion to sync my iphone and i want a common disc space to share music.  The problem i am having is the first step.  I am using gparted to resize my existing ext3 partion so i have room to create the new windows partion and shared partion.  However, when i try to unmount ext3 it says:

Could not unmount /dev/sda1

The partition could not be unmounted from the following mountpoints:

/

Most likely other partitions are also mounted on these mountpoints. You are advised to unmount them manually.


What do i have to do to fix this issue so i can install windows before the registration window closes.  Thank you all in advance.

---

### Post by drs305 on 2009-02-08
If you are trying to resize your system (/) partition, you can only do so when it is unmounted. Since you can't unmount the system and use it at the same time, you have to run gparted from the ubuntu LiveCD or from a third-party CD with gparted on it - such as the gparted CD or the SystemRescueCD.

Back up important data before any repartitioning.

---

