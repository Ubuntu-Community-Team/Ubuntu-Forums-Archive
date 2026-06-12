---
title: "Remove Windoes partition from places menu"
date: 2009-05-03
forum: Desktop Environments
---

### Post by swisstone198 on 2009-05-03
I've searched everywhere but can't find how to remove my Windows partition from the places menu on Jaunty. The volume isn't mounted and I can't remove it within Nautilus. I have a Windows recovery volume and that doesn't show in the menu. I have search through /etc and /home but can't find any config files that refer to either drive. 

Can anyone help please?

---

### Post by damphoud on 2009-05-03
Head to Synaptic Package Manager and install "startupmanager" to manage your list.

To change the list, you can head to /boot/grub/menu.lst

Follow about 3/4 the way down, after "## ## End Default Options ##", and delete the old Windows partition.

You can make a copy inside the /grub folder, in case you make a mistake.



OOPS, disregard my reply... I thought you had a grub issue...

---

### Post by swisstone198 on 2009-05-08
Anyone got any ideas?

---

### Post by mcduck on 2009-05-08
If you don't want to ever access the Windows partition form Ubuntu you can just remove it from /etc/fstab (which is the file that tells what partitions to mount and where to mount them).

If you still want n to be able to access that partition, but just don't want it to show in desktop or the places-menu, you'll have to chnage the fstab to mount the drive into any other location than /media.

If you want exact instructions for what to remove/change, post contents of the /etc/fstab file here.

---

### Post by swisstone198 on 2009-05-08
Thanks.

---

