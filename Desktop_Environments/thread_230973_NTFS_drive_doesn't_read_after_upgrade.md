---
title: "NTFS drive doesn't read after upgrade"
date: 2006-08-06
forum: Desktop Environments
---

### Post by pr0-t31n on 2006-08-06
After I upgraded to dapper from breezy, My windows drive isnt mounted, or isnt readable. It does recognize a 76.7 GB volume but when i double click on it says
> Unable to mount the selected volume. 
then i hit more info and gives me this
> mount: only root can mount /dev/sda1 on /media/hda1

---

### Post by Sutekh on 2006-08-06
Unless there is another way I don't know about, you will need to do some editing of the /etc/fstab, which is used to configure the location, options of mountable partitions.

You can edit it so that an ordinary user (not root) can mount and unmount partitions, using the **user** flag.

First open a Terminal window (Applications -> Accessories menu) and then use these commands to backup and edit the file
```
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` Then find the line that corresponds to the Windows partition (/dev/sda1 by the look) and then in the options part of the line add the word **user**.  It should look something like this when you are done, this is from my /etc/fstab so don't worry about small differences.
```
/dev/sda1   /mnt/windows   ntfs   nls=utf8,umask=0222,**user**   0    0
``` Then save the file using Ctrl+O and then exit the nano editor using Ctrl+X.

Are you able to mount it now by double-clicking?

---

### Post by pr0-t31n on 2006-08-06
nope, thanks but same error

---

### Post by curtis1005 on 2006-08-09
Try this also:

sudo mkdir /media/usb01

add following row into /etc/fstab
/dev/sda1    /media/usb01   ntfs   nls=utf8,umask=0222,users   0   0


it works for me

---

