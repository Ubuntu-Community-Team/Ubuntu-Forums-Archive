---
title: "Mapping a network drive"
date: 2006-07-14
forum: Desktop Environments
---

### Post by SonicSteve on 2006-07-14
Hi there,
I'm sure that this has been asked in some other thread but..can't find it if it has.
Can Ubuntu map a network drive like windows. I found the option to "make link" but doing this doesn't quite have the same effect.

for instance, I have  my MP3's shared on a windows box. I can see the share and connect to it. I can link to it and have the icon on the desktop. But If I run a media player it can't see the resource to play the files. The programs don't have options to look at a network resource to get files. 
So I was hoping that there was a way to do this.

---

### Post by slider on 2006-07-15
Basically what you need to do is mount the samba shares using the mount command or do it at startup by modifying the /etc/fstab file. There are a number of threads here discussing it. Search on smbfs , mount and fstab .

On Edit:

Even better I found this

[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by SonicSteve on 2006-07-15
thanks slider,
I guess I'm starting to understand linux I actually thought that it might have something to do with the fstab file. I just didn't know it had to do with mounting a samba share.
What confused me was the "make link" option.

Thanks!

---

