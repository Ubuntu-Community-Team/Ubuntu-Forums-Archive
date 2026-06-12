---
title: "Transfer Ubuntu + all settings?"
date: 2006-09-01
forum: Desktop Environments
---

### Post by markcholden on 2006-09-01
I'm in the midst of doing some major partition work on my hard drive. I've got a dual-boot PC, and Ubuntu currently resides in an Ext3 partition inside of an extended partition. I deleted a few old partitions, and now I'd like to move it to a primary partition and and resize it. As far as I can see there is no way I can do this without having to reinstall Ubuntu. But I don't want to lose all my settings and downloaded programs, it would be a pain in the *** to set everything up again. So is there any way I can transfer Ubuntu and all settings? Can I, for example, burn the entire contents of the partition to a DVD then copy it back over in WinXP?

---

### Post by Rui Pais on 2006-09-01
hi,
the simple way is use a liveCD and plain cp command with -a (archive) flag to preserve permissions and ownership.

Make the new partition with the desired size from the LiveCD (using gparted is simpler) mount both partition old and new and do:
```
sudo cp -a /mnt/oldubuntu/* /mnt/newubuntu/
```
Where /mnt/oldubuntu and /mnt/newubuntu, are the name of mount points (choose the ones you like, of course).

Then edit /mnt/newubuntu/etc/fstab line of / (root entry) to the new /dev/hdXX.

Edit your grub menu.lst and add/edit a new entry, equal to old one except the new /dev/hdXX.

reboot and enjoy :)

---

### Post by markcholden on 2006-09-01
Sorry, I did not follow that. I'm a Linux and Ubuntu newb. Can you explain in more detail?

---

### Post by Rui Pais on 2006-09-01
> **markcholden said:**
> Sorry, I did not follow that. I'm a Linux and Ubuntu newb. Can you explain in more detail?

No problem.
For simplicity do you mind to say me which partition (hd??) is your actual Ubuntu, which one you want to be the new one and where your boot partition his?

---

### Post by aysiu on 2006-09-01
One of these might help:
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

### Post by markcholden on 2006-09-01
My hard drive looks like this:

```
* Windows partition (NTFS)
* extended partition
   * Linux Ext3
   * Linux swap
```

I want it to look like this:

```
* Windows partition
* Linux Ext3
* Linux swap
* Shared data partition
```

Is there any way I can do that and keep all my settings and downloads in Ubuntu?

---

### Post by markcholden on 2006-09-01
Oh, excellent, aysiu! We cross posted. That's exactly what I'm looking for. Thanks!

---

