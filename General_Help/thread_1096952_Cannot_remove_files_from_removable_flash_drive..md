---
title: "Cannot remove files from removable flash drive."
date: 2009-03-15
forum: General Help
---

### Post by BlocknBleed on 2009-03-15
I loaded some mp3 files onto a microSD card and now I can't delete them. It says I don't have owner permission to do anything but read only. I put the files there and now I can't modify them.  When I try to change permissions my root password doesn't work. 

What am I doing wrong?

---

### Post by taurus on 2009-03-15
Is it fat32/vfat filesystem?

```
sudo fdisk -l
df -h
```
See if you can remove them with nautilus.

```
gksudo nautilus
```

---

### Post by BlocknBleed on 2009-03-15
looks like FAT16 of all things. I could format it if I knew how.

The gksudo nautilus didn't help.

---

### Post by taurus on 2009-03-15
Is it /dev/sdb1?

---

### Post by BlocknBleed on 2009-03-15
> **taurus said:**
> Is it /dev/sdb1?

/dev/sdc1

---

### Post by taurus on 2009-03-15
Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
mount
```

---

### Post by BlocknBleed on 2009-03-15
> **taurus said:**
> Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
mount
```[ATTACH]106490[/ATTACH]

[IMG]http://http://ubuntuforums.org/attachment.php?attachmentid=106490&stc=1&d=1237140255[/IMG]

[ATTACH]106492[/ATTACH]

---

