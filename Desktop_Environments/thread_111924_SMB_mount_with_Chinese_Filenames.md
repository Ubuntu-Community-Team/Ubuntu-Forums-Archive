---
title: "SMB mount with Chinese Filenames"
date: 2006-01-03
forum: Desktop Environments
---

### Post by mosestruong on 2006-01-03
I have a Maxtor Shared Storage which contains Chinese Filenames, when I mount using cifs as the filesystem, the Chinese filenames are displayed correctly. However I couldn't get the permissions correct.

If I mount using smbfs, I could get the permissions correct but chinese filenames becomes unreadable

below are two examples of what I put in the fstab file:
//dan/giai	/dan/giai	cifs	credentials=/root/.smbcredential,iocharset=utf8,rw,dir_mode=0777,file_mode=0666,umask=000	0	0
//dan/moses	/dan/moses	smbfs	credentials=/root/.smbcredential,iocharset=utf8,dmask=0777,fmask=0666,umask=000	0	0

Would anyone know how I could get the permissions and the Chinese filenames to display correctly. Thank you.

---

### Post by mosestruong on 2006-01-31
I'm wondering if anyone out there might know how Nautilus mount window shares? does anyone know how it works out what filesystem type to use and what options it uses?

Coz I'm trying to do the same thing with /etc/fstab...

---

### Post by qiet72 on 2006-07-03
Try this in fstab:

//<server>/<share> <mountpoint> smbfs  credentials=/home/<username>/.smbcredentials,lfs,uid=<username>,gid=<group>,codepage=unicode,iocharset=utf8,unicode

or on command line:

sudo mount -t cifs  //server/share <mountpoint> -o username=<username>,uid=<uidofuser>,gid=<gidofuser>,iocharset=utf8

Hope this helps!

---

### Post by mosestruong on 2006-07-20
Thanks for the tip... i feel like im getting somewhere again:)

After using the options ```
-o iocharset=utf8,codepage=unicode,unicode
``` the chinese filenames are now visible... 

But if i don't specify uid or gid, then the ASCII is not shown, but as 
": x 7 9" (no spaces - added to the smilies won't get in the way...)

 etc.
However, since I can't use cifs for the exact reason that I need to override the uid and gid, your suggestion is exactly what I've been searching for the past few months!!!

Thank you so much qiet72!!!

---

