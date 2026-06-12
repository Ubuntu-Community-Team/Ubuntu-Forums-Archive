---
title: "fstab is empty"
date: 2006-07-14
forum: Desktop Environments
---

### Post by torypatnoe on 2006-07-14
I posted to the Installation forum and didn't get a response. I'm reposting here.

I just installed a clean ubuntu-dapper box on a Dell laptop. I received a disk from a friend so I don't know if it was the official release.

I then applied all updates and upgraded to the linux-686 package (which runs slower). Most things work fine except the /etc/fstab contains only one line:

# UNCONFIGURED FSTAB FOR BASE SYSTEM

Commands like df -h do no return any reference to the root file system. I cannot determine the size of the / partition. I used the default installation with / and swap only. Root is mounted as xfs.

Is there a way to correct this problem? Is this a problem?

Thanks
Tory

---

### Post by llamakc on 2006-07-14
You can see how the disk is partitioned with:

sudo fdisk -l /dev/hda

or /dev/hdb, /dev/sda depending on your setup.

---

### Post by torypatnoe on 2006-07-14
I didn't have much on the machine to begin with. It also appears the grub doesn't like a root xfs (which is why ubuntu installed lilo). I punted and re-installed with a reisterfs.

Tory

---

