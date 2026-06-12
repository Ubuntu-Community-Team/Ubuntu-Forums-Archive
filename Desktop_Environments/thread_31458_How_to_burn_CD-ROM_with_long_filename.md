---
title: "How to burn CD-ROM with long filename ?"
date: 2005-05-03
forum: Desktop Environments
---

### Post by gugus on 2005-05-03
Hello all!
I want to burn a CD with some file which are long filename (between 100 and 120 character).
How to do it with the Nautilus Burner ?

thanks,

---

### Post by liljencrantz on 2005-05-03
[QUOTE=gugus]Hello all!
I want to burn a CD with some file which are long filename (between 100 and 120 character).
How to do it with the Nautilus Burner ?

thanks,[/QUOTE]
 I'm not 100% sure, but I don't think Nautilus burned supports the rockridge extensions, burning ext2 filesystems or any other method of burning other than regular ISO cds. Try using K3b.

---

### Post by az on 2005-05-04
* Joliet: Joliet is an extension of the ISO 9660 standard to allow CDs to be written using long filenames and Unicode on Windows. Joliet allows filenames up to 64 characters, including spaces. Joliet is readable by PCs running Windows 95 or later operating systems and Macintosh computers running the Joliet Volume Access extension. Macs will not read Joliet file names longer than 31 characters. Name your files accordingly.
    * RockRidge: RockRidge is an extension of the ISO 9660 standard to allow CDs to be written using long filenames while maintaining Unix file permissions and symbolic links. RockRidge allows filenames up to 127 characters, the underscore symbol ( _ ), but no spaces. RockRidge is readable on a variety of UNIX operating systems.

I am pretty sure that nautilus cd burner uses rock ridge.  Did you have problems with it?

---

### Post by gugus on 2005-05-04
Yes, Nautilus use "rock ridge". And I can have the full filename under Ubuntu.... But not under Windows.
How to configure Nautilus for using the Joliet ?

---

### Post by coderK on 2007-05-26
Is there any way to get joliet for Nautilus?

---

