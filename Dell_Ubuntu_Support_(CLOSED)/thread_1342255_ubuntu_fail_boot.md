---
title: "ubuntu fail boot"
date: 2009-11-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ChaosUK on 2009-11-30
Today i decided to boot up ubuntu but it got to the loading screen and said

one or more of the mounts listed in /etc/fstab cannot be mounted:
/: waiting for /deb/loop0
/tmp waiting for (null)
/boot: waiting for /host/ubuntu/disks/boot
press esc to enter a recovery shell

so i went into the recovery shell, waited 5 minutes and nothing happened.
i'm currently using Windows XP SP3 and 9.10, so can someone help me please?

---

### Post by ChaosUK on 2009-11-30
bamp

---

### Post by ajgreeny on 2009-11-30
Boot to the live CD and show us the output of the /etc/fstab file from your installed system, by mounting the partition, and navigating to the file in nautilus.  Then show the output of ```
sudo fdisk -l
```and finally ```
sudo blkid
``` with all the hard disk partitions mounted.

---

### Post by ChaosUK on 2009-11-30
> **ajgreeny said:**
> Boot to the live CD and show us the output of the /etc/fstab file from your installed system, by mounting the partition, and navigating to the file in nautilus.  Then show the output of ```
sudo fdisk -l
```and finally ```
sudo blkid
``` with all the hard disk partitions mounted.

does it matter that my live disc is 9.04 and my ubuntu is 9.10?

---

### Post by ChaosUK on 2009-11-30
never mind, fixed the problem, but thanks for the help!

---

