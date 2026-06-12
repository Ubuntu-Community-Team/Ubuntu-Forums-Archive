---
title: "Can't mount hard drives?"
date: 2009-04-04
forum: General Help
---

### Post by Wired16 on 2009-04-04
I have 2 320g and one 400g hard drives, but I can't mount them! I've tried force mounting them through the terminal but to no avail. Can anyone help me out?
I think it may be caused by the drives having the NTFS filesystem. 


I used the following command to force mount```
sudo mount -t ntfs-3g /dev/sdc1/media/disk -o force
```

---

### Post by taurus on 2009-04-04
> **Wired16 said:**
> I have 2 320g and one 400g hard drives, but I can't mount them! I've tried force mounting them through the terminal but to no avail. Can anyone help me out?
I think it may be caused by the drives having the NTFS filesystem. 


I used the following command to force mount```
sudo mount -t ntfs-3g /dev/sdc1   /media/disk -o force
```

Is there a /media/disk?  If not, you must create that mount point first before you can mount a drive/partition to it.

```
ls -la /media
sudo mkdir /media/disk
```

Also, there should be a space between /dev/sdc1 and /media/disk.

---

### Post by ShaunG on 2009-04-04
Make sure ntfs-3g is installed.

```
sudo apt-get install ntfs-3g
```

Then make sure that teh mount point exists.

```
sudo mkdir /media/disk
```

Then mount

```
sudo mount -t ntfs-3g /dev/sdc1 /media/disk
```

Also make sure that the device you are mounting actually is at /dev/sdc1

You can check this by running

```
fdisk -l
```

---

### Post by Wired16 on 2009-04-04
Thank you SO much! Worked like a charm!

---

