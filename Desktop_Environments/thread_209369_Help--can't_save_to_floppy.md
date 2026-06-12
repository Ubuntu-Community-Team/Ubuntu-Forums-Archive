---
title: "Help--can't save to floppy"
date: 2006-07-05
forum: Desktop Environments
---

### Post by Jillybean on 2006-07-05
Hi there.  Figured out how to mount my floppy and can copy files from the floppy to desktop, but I can't save a file to the floppy as it says I don't have permission?  Can someone help?
Thanks,
Jill

---

### Post by vidak on 2006-07-05
[QUOTE=Jillybean]Hi there.  Figured out how to mount my floppy and can copy files from the floppy to desktop, but I can't save a file to the floppy as it says I don't have permission?  Can someone help?
Thanks,
Jill[/QUOTE]
Well, from console you probably do that using 
mount /media/floppy
 or something similar... Do you get some message here (like media is write protected, mounting read-only)? In this case check whether the floppy isn't write protected... If you mounted it using 
sudo mount /dev/fd0 /media/floppy
then only root can write to it.
Anyway, check if you can write to it as root, eg. try sudo touch /media/floppy/foo
(if this doesn't work, the floppy is write protected).

You could check /etc/fstab, too for the floppy's mount options (is there the 'user' option?)

good luck!

---

### Post by Jillybean on 2006-07-05
Hi.  Yes I did mount the disk using the sudo mount -t msdos /dev/fd0 /media/floppy0 command, which I found in these forums.  I did try to use the command you gave, but still when I tried to copy to the disk, the message I get is "Error while copying to "/media/floppy0". You do not have permissions to write to this folder."  How do I copy something to the disk 'as root'?  Thanks a lot for your help,
Jill

---

### Post by Jillybean on 2006-07-05
p.s. I'm not sure how to "check /etc/fstab" as you suggest.  I'm new to this stuff.

---

### Post by vidak on 2006-07-06
[QUOTE=Jillybean]p.s. I'm not sure how to "check /etc/fstab" as you suggest.  I'm new to this stuff.[/QUOTE]

If you want to run something (eg copying a file to a floppy :)) as root, just type 
```
sudo cp foo.txt /media/floppy
```

(note: root is a user which has superuser privileges - the administrator, if you like it so. In ubuntu, there is no root user present for security reasons. When superuser privileges are needed, you have to use sudo.)

/etc/fstab is a file, which contains the mount options of your devices. (you can read the man page of this file using 'man fstab')

To view this file, use 'cat /etc/fstab', 'less /etc/fstab' from console, or any graphical text editor you want.

Did this solve the problem?

---

