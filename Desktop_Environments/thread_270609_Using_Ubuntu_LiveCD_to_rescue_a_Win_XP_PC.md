---
title: "Using Ubuntu LiveCD to rescue a Win XP PC"
date: 2006-10-03
forum: Desktop Environments
---

### Post by jagosilver on 2006-10-03
My sister's Windows PC has stopped working and she can't access any files on it. 

Would it be possible to use a LiveCD to get access to the files on the HD and copy them to a USB HD?

She could then try more drastic methods to get the PC working without worrying about losing files....

Jago

---

### Post by aysiu on 2006-10-03
Yes, a Ubuntu CD *can* be used as a rescue CD, but it is not designed to be one. If you have a Knoppix CD handy, that would be even better.

1. Boot up the live CD

2. Open a [terminal.](http://www.psychocats.net/ubuntu/terminal)

3. Paste in this code: ```
sudo fdisk -l
``` From the output, you should be able to tell where your sister's drive is and what filesystem it is. For the sake of this example, we'll assume it's /dev/hda1 and NTFS

4. Paste in this code: ```
sudo mkdir /media/recovery
sudo mount -t ntfs /dev/hda1 /media/recovery -o nls=utf8,umask=0222
```

5. Plug in the USB drive.

6. Drag the files from /media/recovery to your drive.

If it's something other than /dev/hda1 (/dev/hda2, /dev/hda5), just substitute in the appropriate location. If it's not NTFS (FAT32, for example), change the second mount command to ```
sudo mount -t vfat /dev/hda1 /media/recovery -o iocharset=utf8,umask=000
```

---

### Post by jagosilver on 2006-10-03
Thanks, will give that a try

---

### Post by GreenMarine on 2006-10-03
You might try [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) as well.

---

### Post by jagosilver on 2006-10-04
> **GreenMarine said:**
> You might try [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) as well.
Cheers Green Marine, I'll take a look at that too.

---

