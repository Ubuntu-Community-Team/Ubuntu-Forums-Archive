---
title: "Mount problems"
date: 2005-08-22
forum: Desktop Environments
---

### Post by crt on 2005-08-22
Hi all, Well I tried to mount a couple of my Fat32 drives, I edited the fstab file and added these two lines.

/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0
/dev/hda6       /media/windows  vfat    iocharset=utf8,umask=000   0       0

When I reboot and then try to access the drives through konqueror hda6 will only show up either by accessing hda1 or hda6, even though it shows hda1 mounted when I try to access it, it only shows hda6. 


R

---

### Post by Takis on 2005-08-22
Uh-oh. Don't try mounting them to the same mount point, that could be highly dangerous.
Try mounting them to /media/windows and /media/windows2 or something.

---

### Post by crt on 2005-08-22
Actually I thought of that right after I made the post. Each mount point needs its own folder.


Thanks

Rog

---

