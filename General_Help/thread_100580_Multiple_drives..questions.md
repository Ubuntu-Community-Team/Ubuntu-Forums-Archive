---
title: "Multiple drives..questions"
date: 2005-12-07
forum: General Help
---

### Post by -Navy-SEAL- on 2005-12-07
I am new to Ubuntu and have a few questions about using multiple drives.

I have the install on a 9.1GB SCSI disk (/dev/sda) with a swap partition and the rest of the drive as /

I have three 40GB IDE drives that I would like to set up just for storage. I am just a little confused on what to mount them as though.

---

### Post by psusi on 2005-12-07
Technically you can mount it in the filesystem wherever you choose, but if you mount it in a subdirectory of /media, like /media/hda1, then it will show up on the desktop which you may find helpful.

---

### Post by Bachstelze on 2005-12-07
@psusi > You can put whatever you want on the esktop, not only the stuff in /media

---

### Post by -Navy-SEAL- on 2005-12-07
[QUOTE=psusi]Technically you can mount it in the filesystem wherever you choose, but if you mount it in a subdirectory of /media, like /media/hda1, then it will show up on the desktop which you may find helpful.[/QUOTE]

That is sort of what I was looking for...I guess I just expected the drives to show up under "Computer" along with Floppy, CD and Filesystem, but I take it that isn't how it works in Linux:confused:

---

