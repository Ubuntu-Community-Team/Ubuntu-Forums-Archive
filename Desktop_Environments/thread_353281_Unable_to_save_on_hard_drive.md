---
title: "Unable to save on hard drive"
date: 2007-02-04
forum: Desktop Environments
---

### Post by MosesS on 2007-02-04
Hi

after trying to d/l a file from the net I wanted to save it on a FAT32 USB hard rive that I have but an error came up saying unable to do so. 

ended up saving it at home/myname but this means that the file won't be accessible from Windows.

Any help?

Thanks

---

### Post by taurus on 2007-02-04
How did you mount that USB harddrive?  Try using the sudo command to move it to the harddrive from your $HOME account then.

```
sudo mv **filename** /media/usbdrive
(or wherever you mounted your USB drive...)
```

---

### Post by MosesS on 2007-02-04
I didn't mount it manually, i just plugged it in and after a restart it appeared mounted with an icon on the desktop.

it does show though under /media

I will try and let u know

thanks for the quick reply:)

---

### Post by MosesS on 2007-02-04
Ok tried the command and it works - it will move the file to the FAT32 hdd.

any idea why though I cannot save directly to it?

thanks

---

### Post by taurus on 2007-02-04
Because right now the /media/usbdisk is owned by root so only root can write to it.  If you want to write to it as a regular user, you either need to use the sudo command or remount it with the right permission.

```
sudo umount /dev/sda1
sudo mount -t vfat /dev/sda1 /media/usbdrive -o iocharset=utf8,umask=000
```
Now, see if you can write stuff to /media/usbdrive without using the sudo command.

---

### Post by MosesS on 2007-02-05
I have tried a few things that I believe give now a different picture so the problem might be elsewhere...

Downloading a torrent with KTorrent, it won't allow me to save it on the USB FAT32 drive. 

BUT I can move file in and out of the drive from the "explorer", copy, cut, paste.....kind of full access

What you reckon?

Cheers

---

### Post by stoeptegel on 2007-02-05
> **MosesS said:**
> I have tried a few things that I believe give now a different picture so the problem might be elsewhere...

Downloading a torrent with KTorrent, it won't allow me to save it on the USB FAT32 drive. 

BUT I can move file in and out of the drive from the "explorer", copy, cut, paste.....kind of full access

What you reckon?

Cheers

Fat32 file system and symlinks are not that much of a friend. If the USB drive would have a modern GNU/Linux filesystem it would most probably just work.

---

