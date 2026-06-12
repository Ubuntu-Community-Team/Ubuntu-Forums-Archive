---
title: "Mounting a read only file system Ubuntu 10.04"
date: 2011-01-28
forum: Desktop Environments
---

### Post by metallica1973 on 2011-01-28
I made a modification to the /etc/fstab using Ubuntu 10.04 and now it wont boot correctly. I can get the cli but when I enter /etc/fstab and make an edit it says" changing permission of /etc/fstab: read only file system"

How can I mount the partition so that I can edit it? thanks in advance

---

### Post by pastalavista on 2011-01-28
You need to use 'sudo' to edit system files ```
sudo gedit /etc/fstab
``` To learn about fstab, check out [this post]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by metallica1973 on 2011-01-28
I cant boot into to the OS just from recovery mode and from the their it gives me that error. there is no GUI

---

### Post by pastalavista on 2011-01-28
From the console, you'll need to use 'nano' to edit files```
sudo nano /etc/fstab
```

---

### Post by sisco311 on 2011-01-28
> **metallica1973 said:**
> I made a modification to the /etc/fstab using Ubuntu 10.04 and now it wont boot correctly. I can get the cli but when I enter /etc/fstab and make an edit it says" changing permission of /etc/fstab: read only file system"

How can I mount the partition so that I can edit it? thanks in advance

Try to remount the root partition:
```
sudo mount -o remount,rw /
```

---

### Post by metallica1973 on 2011-01-28
[PHP]/dev/sdb1:clean 123412/878586 files, 8685856/23523526 blocks
mount: / not mounted already, or bad option
mountall: Filesystem could not be mounted: /
An error occurred while mounting /
Press S to skip mounting or M for manual recovery  [/PHP]

I added notaime option to my fstab by accident


so if I choose manual I get to the cli and whenever I attempt to edit the file I get the above error. I used another machine and attempted to mount the drive but I get the same error.

I tried 

[php]sudo mount -o remount,rw /[/php]

and I get 

[php]EXT4-fs (sdb1): unrecognized mount option "notaime" or missing value
mount: / not mounted already, or bad option[/php]

---

### Post by metallica1973 on 2011-01-28
issue resolved:

I mounted the the drive on another system and just:

[php]chown root:root /media/usbdisk/etc/fstab[/php]

corrected the "notaime" to "noatime", reboot the usbstick and all is well. I guess I didnt need to chown back the /etc/fstab to root since it is already root. It seems to have worked.

---

