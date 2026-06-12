---
title: "Cannot get USB HDD to work..."
date: 2006-04-13
forum: Desktop Environments
---

### Post by dmbatcu on 2006-04-13
I cannot get my USB hard drive to work properly in kubuntu. I opened up gparted and set the whole hard drive to ext3. I mount it through the terminal but when I try to access/add files to it, I get the following error message: Could not mount device. The reported error was: mount: I could not determine the filesystem type, and none was specified>  Any ideas? I need to be able to back up important documents.

---

### Post by Sutekh on 2006-04-13
Try specifying the filesystem type
```
sudo mount /dev/sda1 /media/usbmount **-t ext3**
```


This assuming that /dev/sda1 is the USB partition, use ```
sudo fdisk -l
``` to determine this and that /media/usbmount is where you want to mount the USB drive, use ```
sudo mkdir /media/usbmount
``` to create the folder.

---

### Post by dmbatcu on 2006-04-13
Thank you for the help so far.

I did what you asked. I tried to move a folder and its contents (School) from the desktop to /media/usbmount. 

```
Access denied to /media/usbdisk/School.
```

Next, I ran the following command

```
sudo chmod 777 -R /media/usbmount
```

I still get the same error.

I also tried:

```
sudo chmod 777 -R /dev/sda1
sudo chmod 777 -R /dev/sda
```

---

### Post by Sutekh on 2006-04-13
Ok, what's the output from ```
sudo fdisk -l
```and ```
ls -l /media
```

---

### Post by dmbatcu on 2006-04-13
```
sudo fdisk -l
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9729    78148161   83  Linux
daniel@ptkfgs:~$

```
ls -l /media
```

lrwxrwxrwx  1 root   root      6 2006-04-13 21:03 cdrom -> cdrom0
drwxr-xr-x  2 root   root   4096 2006-04-13 21:03 cdrom0
drwxr-xr-x  2 root   root   4096 2006-04-13 21:03 cdrom1
drwxrwxrwx  3 daniel daniel 4096 2006-04-13 23:27 usbdisk
drwxr-xr-x  2 daniel daniel 4096 2006-04-13 22:45 usbmount

Before I received your post, I changed ownership (sudo chown daniel:daniel -R /media/usbmount), and it now works, but that does not seem to be working as intended. Also, how can I set up fstab for it to automount on startup?

---

### Post by Sutekh on 2006-04-13
To set it up in the /etc/fstab you need to unmount it first```
sudo umount /dev/sda1
```then add this line to your /etc/fstab
```
/dev/sda1   /media/usbdisk   ext3   defaults   0   0
```
Then use```
sudo mount -a
```
to remount it again.  This will automount on startup too.

---

### Post by dmbatcu on 2006-04-14
Thanks for all the help Sutekh, i'm almost 100% free of Windows :)

---

### Post by Sutekh on 2006-04-14
[QUOTE=dmbatcu]Thanks for all the help Sutekh, i'm almost 100% free of Windows :)[/QUOTE]
Your most welcome.  So whats stopping you? 

Only kidding!  I can't talk yet! :)

---

### Post by dmbatcu on 2006-04-14
Connecting to my university's Protected EAP (PEAP) wireless network. I've made a thread about it but a solution does not seem evident.

---

