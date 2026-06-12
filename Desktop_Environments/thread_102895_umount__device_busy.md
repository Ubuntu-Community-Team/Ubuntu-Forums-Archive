---
title: "umount : device busy"
date: 2005-12-13
forum: Desktop Environments
---

### Post by Morrigu on 2005-12-13
I can't seem to unmount and eject my dvd disc. I have seem to run out of ideas what to do with this.

```

lindmmik@none:~$ sudo umount -f /media/cdrom0
umount2: Device or resource busy
umount: /media/cdrom0: device is busy
umount2: Device or resource busy
umount: /media/cdrom0: device is busy

lindmmik@none:~$ sudo fuser /media/cdrom0
/media/cdrom0:

lindmmik@none:~$ sudo lsof | grep cdrom
lindmmik@none:~$

```

---

### Post by frodon on 2005-12-13
You can get this result if you have an apps opened which use the cdrom (it could be nautilus !).

---

### Post by Morrigu on 2005-12-13
I've closed all apps on desktop, but that didn't help. Should I just force the damn thing open with paper clip?

---

### Post by frodon on 2005-12-13
And what do you get if you run this command ? :  ```
sudo eject cdrom0
```

---

### Post by lutrafobic on 2005-12-13
you tried: ```
sudo umount -l /media/cdrom0
``` ?

---

### Post by Morrigu on 2005-12-13
```

lindmmik@none:~$ sudo eject /media/cdrom0
umount: /media/cdrom0: device is busy
umount: /media/cdrom0: device is busy
eject: unmount of `/media/cdrom0' failed
lindmmik@none:~$ sudo umount -l /media/cdrom0
lindmmik@none:~$ sudo eject /media/cdrom0
lindmmik@none:~$

```

after umount -l the eject command worked. I still have the icon for the dvd on my desktop, and right click + eject didn't work on the desktop.

Also I can't read properly other dvd:s. I won't get icon on desktop when I insert new disc, and mounting manually will give this:

```

lindmmik@none:/media$ sudo mount /dev/hdc /media/cdrom0
mount: block device /dev/hdc is write-protected, mounting read-only
lindmmik@none:/media$ cd cdrom0
lindmmik@none:/media/cdrom0$ ls
???  ????   ?????  ?????  ?????   ??????
???  ?????  ?????  ?????  ??????  ??????

```

---

### Post by mcpish on 2006-03-09
I have the EXACT same problem unmounting DVD's sometimes in Ubuntu.  It seems picky sometimes and I don't know why sometimes I can't unmount and othertimes I get the errors you do.

I also tried the method here with the "sudo umount -l" command it also lets me eject the disc finally but I'm stuck with the old icon on the desktop.  

The only solution is a reboot which I "shouldn't have to do in Linux", so there be some more elegant way of doing this.

---

### Post by mcpish on 2006-03-09
Ok I think I fixed it

after ejecting the CD using the method above with Sudo  you'll be stuck with the old icon on you desktop.  Now use the following command WITHOUT using sudo:

> 
umount /media/cdrom0


then the icon will disappear and you should be able to now use another disc

---

