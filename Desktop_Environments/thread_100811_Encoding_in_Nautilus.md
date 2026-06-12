---
title: "Encoding in Nautilus"
date: 2005-12-08
forum: Desktop Environments
---

### Post by banjobacon on 2005-12-08
I'm experiencing a problem with filenames in Nautilus. I have an NTFS formated hard drive mounted which contains music. I wanted to copy some of this music on to my iRiver. One album I wanted to copy is called *D&#233;j&#224; Vu*. However, Nautilus displays "D?j? Vu (invalid encoding)". When I try to copy and paste the folder into my iRiver, i get an error, which I assume has to do with the encoding because it's not a matter of not having the space.

However, my iRiver has the album *Med&#250;lla* by Bj&#246;rk on it, and both the artist name and album title show up without encoding errors. Why are these errors exclusive to the files on the NTFS drive, and is there any way to fix this? I'd like to be able to copy and paste these folders without a problem, at the very least.

---

### Post by magnusbb on 2005-12-08
This I have in my fstab:

/dev/hda2 	/media/hda2 	ntfs 	umask=0222 	0 	0

And it works with those characters you're mentioning.

On my vfat partition I had to do add **iocharset=utf8** to get that support.

---

### Post by banjobacon on 2005-12-08
My fstab entry is:

/dev/hdb1       /windows/d      ntfs    umask=0222      0       0

Looks the same to me.

---

### Post by sipstar on 2005-12-11
The "iocharset=utf8" solved the encoding problem for me. Thank you very much! :D

---

