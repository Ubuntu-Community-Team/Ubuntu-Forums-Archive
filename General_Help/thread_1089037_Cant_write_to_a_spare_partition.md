---
title: "Cant write to a spare partition"
date: 2009-03-06
forum: General Help
---

### Post by W2IBC on 2009-03-06
OK, well I decided to make a partition on my drive so i could store items/music/ect and if i needed to re-install i could without losing the important items. unfortunately it wont let me write to the partition (and i totally forget how i got it to last time)

my setup
HDA1 -main os
HDA2 -spare blank partition

the "disk" is under root. how can i change the disk to my user acct.

---

### Post by taurus on 2009-03-06
What filesystem is /dev/hda2?  

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

If it's ext3, you can change the ownership of the mount point for /dev/hda2 from root to your login name.

_Assuming_ you have mounted /dev/hda2 to /media/hda2 and your login name is account, you would do

```
sudo chown -R account:account /media/hda2
ls -la /media
```

---

