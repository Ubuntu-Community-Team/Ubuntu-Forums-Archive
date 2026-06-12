---
title: "unable to mount fdd unit and..."
date: 2005-09-07
forum: Desktop Environments
---

### Post by doxelupo on 2005-09-07
I've just installed ubuntu 5.04 on a notebook provided with a floopy drive but I can't mount my floppy drive, it doesn't appear in the computer's resources and so I cannot mount it.
But strangely the format option is active and is working correctly. it works on /dev/fd0 , if I try to access the disk non way! What's wrong? Could you please help me solving this?

The same notebook has got an intel 537 modem installed on board, are there drivers for it?

thanks for the collaboration

---

### Post by John.Michael.Kane on 2005-09-07
[http://www.alwanza.com/howto/linux/floppy.html](http://www.alwanza.com/howto/linux/floppy.html)

mount /dev/fd0 /mnt/floppy

This may help not sure since i dont have a floppy.

---

### Post by Steve1961 on 2005-09-07
First make sure you have an entry in the fstab file that looks something like this:

/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

View the file by typing cat /etc/fstab.  If the entry isn't there first check that the /media/floppy0 directory exists.  If not, create it.  Then edit the fstab file by adding this line.  You can edit the file by typing sudo gedit /etc/fstab and then pasting in the line.  After this type sudo mount -a.  You should now have a working floppy drive.  If you still have problems just change the auto entry to vfat and that should do it.

---

### Post by doxelupo on 2005-09-08
thank you, the floppy  fstab entry didn't exist, I fixed it, and the floppy 's is fully accessible

---

### Post by Steve1961 on 2005-09-09
Pleased to have been of help.

---

### Post by thepcdoctor on 2005-09-11
If the entry isn't there first check that the /media/floppy0 directory exists. If not, create it.
How do I do this??

---

### Post by Steve1961 on 2005-09-11
Just type mkdir /media/floppy0

---

### Post by thepcdoctor on 2005-09-11
Thanks that worked but clicking on floppy gives me:
 
"Unable to mount the selected volume.mount: I could not determine the filesystem type, and none was specified"

????

---

### Post by thepcdoctor on 2005-09-11
It's ok. I fiddled around and found the right click mount/unmount option and now works. Thanks

---

