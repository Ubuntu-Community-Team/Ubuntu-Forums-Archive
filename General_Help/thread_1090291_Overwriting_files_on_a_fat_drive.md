---
title: "Overwriting files on a fat drive"
date: 2009-03-08
forum: General Help
---

### Post by Skerit on 2009-03-08
I'm trying to overwrite a bunch of files on an old fat drive.

For some dark reason it's unable to do this: it can't copy the file because it already exists.

Does anyone know what's going on here? I do believe it's a fat16 drive. It's mounted with the regular rw,auto,... options in fstab

---

### Post by Chandler258 on 2009-03-08
Have you tryed to scan that disk with an utility? Like ... [these]("http://felipecruz.com/linux-disk-utilies.php").

---

### Post by Skerit on 2009-03-08
There wasn't anything wrong with the drive, really. 
I've widened my search a bit and I came up with this fstab entry, which seems to do the trick:

/dev/hda1 /mnt/win_c vfat defaults,users,umask=0,iocharset=iso8859-15,codepage=850 0 0

---

