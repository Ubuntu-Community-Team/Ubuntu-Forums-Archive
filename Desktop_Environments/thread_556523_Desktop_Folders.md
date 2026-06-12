---
title: "Desktop Folders"
date: 2007-09-21
forum: Desktop Environments
---

### Post by Geffers on 2007-09-21
On installing Feisty recently it automatically gave me 5 links on my desktop to Windows partitions.

I would like to move these into one folder, I can see from the properties that they somehow link to /media/hda and /media/hdb but cannot fathom how to move them - drag and drop don't seem to work.

Geffers

---

### Post by jnorthr on 2007-09-21
does not work on mine either. May be a permissions issue ? Dunno...

---

### Post by Wolki on 2007-09-21
> **Geffers said:**
> On installing Feisty recently it automatically gave me 5 links on my desktop to Windows partitions.

I would like to move these into one folder, I can see from the properties that they somehow link to /media/hda and /media/hdb but cannot fathom how to move them - drag and drop don't seem to work.


Mounted drives appear on the desktop automatically.

One thing you could do is to disable showing mounted volumes on the desktop (alt-f2, "gconf-editor", search for "/apps/nautilus/desktop/volumes_visible", uncheck it). This will also mean that usb drives and cds won't appear on the desktop anymore.

Another possibility, though I'm not sure it still works on current versions, is to mount these into directories outside of /media/ or /mnt/. For example you could create a directory called windows ("sudo mkdir /windows", create folders for every partition there ("sudo mkdir /windows/hda1" or how you want them to be named), change your /etc/fstab to point to the new directories instead of the old ones (if your fstab does not contain entries for the old ("/media/hda1" and so on) mount points, tell me and we'll add them), then umount the existing directories and mount the new ones.
This method used to work in the past, I'm not sure it still works but I think it should.

---

### Post by Happy_Man on 2007-09-21
You will need to use nautilus with admin permissions in order to edit the /media folder. Be warned, though, that if you move the /media stuff, it will only stay until you reboot unless you edit the /etc/fstab file. Also, you will need to manually link the folder you make to the desktop if you want to access it like that. If you still want to, though, press alt-f2 and enter:
```
gksudo nautilus
```

And using that, go to the /media folder and rearrange.

---

### Post by Geffers on 2007-09-22
Thanks for info folks, it is not a major issue but I recall putting MS_Windows drives in a folder of my own choice under Breezy.

Geffers

---

### Post by Wolki on 2007-09-22
Can you post your /etc/fstab?

It might be that new versions don't require entries in the fstab anymore (I didn't reinstall since breezy so I'm a bit out of touch with how things work out of the box now, but I do remember that this was planned some time ago)

If that's the case, your internal hard drives are treated exactly like external hard drives and mounted automatically (or at least shown). Still, you should probably be able to place them where you want like I described.

---

