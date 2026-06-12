---
title: "[SOLVED] setting permissions"
date: 2008-12-17
forum: General Help
---

### Post by tsucol11 on 2008-12-17
Need to set permissions but unsuccessful so far. 

System setup:

- Ubuntu 8.10 installed on external hard drive (sdc). Grub also installed on external HD (sdc). 
- / on primary partition, swap & /home on logical partition.
- created a new primary partition (/files) on sdc using gparted.

Partition is visible using nautilus but I am unable to copy to or delete file from the partition without going sudo.

Question: how do I set up permissions so that my /files partition is available for sharing & without using sudo  .

Thank you

Brian

---

### Post by Titan8990 on 2008-12-17
Change the ownership of /files and its children:


sudo chown -R YOURUSERNAME /files

---

### Post by taurus on 2008-12-17
What filesystem is the partition that mounted to /files?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by tsucol11 on 2008-12-17
> **taurus said:**
> What filesystem is the partition that mounted to /files?

```
sudo fdisk -l
cat /etc/fstab
df -h
```


ext3

Brian

---

### Post by tsucol11 on 2008-12-17
> **Titan8990 said:**
> Change the ownership of /files and its children:


sudo chown -R YOURUSERNAME /files

got it working thanks

# going to root
sudo su
chown -R newton /media/files

I didn't realize that gparted would add the files partition to /media

thank you

Brian

---

### Post by vanadium on 2008-12-17
```
I didn't realize that gparted would add the files partition to /media

```
gparted does not add your files nowhere. Probably, your drive is not included in /etc/fstab. Thus, it is not mounted at startup time. It is only mounted when you click on the drive in nautilus. Such "automatic" mounts are always under /media.

If you want to mount your drive permanently at startup, you can include it in /etc/fstab. Then, you can mount it anywhere, although conventionally, you should mount it under either /media or /mnt. In the first case, an icon will be displayed on your desktop. In the second case, the drive will be mounted without having an icon on the desktop (unless you create a symbolic link or a gnome starter yourself).

---

### Post by tsucol11 on 2008-12-17
> **vanadium said:**
> ```
I didn't realize that gparted would add the files partition to /media

```
gparted does not add your files nowhere. Probably, your drive is not included in /etc/fstab. Thus, it is not mounted at startup time. It is only mounted when you click on the drive in nautilus. Such "automatic" mounts are always under /media.

If you want to mount your drive permanently at startup, you can include it in /etc/fstab. Then, you can mount it anywhere, although conventionally, you should mount it under either /media or /mnt. In the first case, an icon will be displayed on your desktop. In the second case, the drive will be mounted without having an icon on the desktop (unless you create a symbolic link or a gnome starter yourself).

Thank you for the correction. All I can say is that when I changed the ownership of the new partition "files" I found it under /media/files ie chown -R newton /media/files. 

At present everything works fine. As for mounting it permanently at start up thank you for the tip.

Brian

---

### Post by tsucol11 on 2008-12-17
I would like to thank everyone who responded. Much appreciated.

Now how do I set this problem as solved:guitar:

Brian

---

### Post by tsucol11 on 2008-12-17
Thanks again

Brian

---

### Post by Bertik on 2009-03-28
Thank you,

worked for me too.

> **Titan8990 said:**
> Change the ownership of /files and its children:


sudo chown -R YOURUSERNAME /files

---

