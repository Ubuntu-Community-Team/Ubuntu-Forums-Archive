---
title: "Problems accessing data on external storage from some applications"
date: 2009-02-17
forum: General Help
---

### Post by Tootler on 2009-02-17
I have just installed ubuntu. I have my data on another partition of the hard drive formatted as fat32 so the data can be shared with windows. 

In some applications, the file/open dialog box shows both the home directory and the external devices, including the data partition, cdrom drive & usb sticks (if I have one plugged in). In other applications - most notably Open Office - file/open only shows the home directory and I cannot seem to find any way of getting to the partition with the files I want to open. 

How can I access external devices in the latter types of application?

Geoff

By the way, I spent hours hunting round trying to find an answer to this.

---

### Post by taurus on 2009-02-17
Have you mounted that fat32/vfat partition while you're in Ubuntu?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by Tootler on 2009-02-17
> **taurus said:**
> Have you mounted that fat32/vfat partition while you're in Ubuntu?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

Yes I had.

I found the files. I was trying to sort another issue and I found that you had to look in /media/partition_name and there they all were.

Thanks for your suggestion anyway.

Geoff

---

