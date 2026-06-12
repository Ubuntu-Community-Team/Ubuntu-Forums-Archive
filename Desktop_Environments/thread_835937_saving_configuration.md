---
title: "saving configuration"
date: 2008-06-21
forum: Desktop Environments
---

### Post by jakub12 on 2008-06-21
A have managed to mount an existing ntfs raid 0 partition, so that it appears on my desktop and is accessible to read and write. 
The only problem I have now is that I don't know how to save this configuration so that I don't have to remount it every time I reboot my Ubuntu session (I know its a silly newbie question).
Here are the commands in case anybody is interested:

sudo dmraid -ay
RAID set "nvidia_ibfbejec" already active
RAID set "nvidia_ibfbejec1" already active

sudo mkdir /media/raid   
sudo mount -t ntfs /dev/mapper/nvidia_ibfbejec1 /media/raid

Thanks,
Jakub

---

### Post by Rocket2DMn on 2008-06-21
You will need to add the partition to /etc/fstab - see [uhelp]community/Fstab[/uhelp]
You can check your Fstab entry with me if you'd like, it will be something like:
```
/dev/mapper/nvidia_ibfbejec1 /media/raid ntfs-3g defaults,locale=en_US.utf8 0 0
```
I'm not entirely sure if any more is needed because it is a RAID partition.

---

### Post by jakub12 on 2008-06-22
Thanks, that did it!!!
Jakub

---

