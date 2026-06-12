---
title: "Problems with ò à ù è é ì"
date: 2005-05-11
forum: Desktop Environments
---

### Post by supermarchino on 2005-05-11
If a file name on a FAT32 or smbfs device contains those letters, I have problems in having it showed up. Mounting with iocharset=iso8859-15,codepage=850 did not seem to help.

---

### Post by supermarchino on 2005-05-11
:roll:

---

### Post by Julius on 2005-05-11
mmm

```

/dev/hda1       /media/windows	ntfs    umask=0222,nls=utf8      0       0

```

THat's what I have in my fstab :P 

the nls=utf8 is the key :P
It works!!

---

### Post by supermarchino on 2005-05-11
[QUOTE=Julius]mmm

```

/dev/hda1       /media/windows	ntfs    umask=0222,nls=utf8      0       0

```

THat's what I have in my fstab :P 

the nls=utf8 is the key :P
It works!![/QUOTE]
mmm 
are you italian?  :grin:  :wink:

---

