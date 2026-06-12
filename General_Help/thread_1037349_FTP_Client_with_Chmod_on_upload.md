---
title: "FTP Client with Chmod on upload"
date: 2009-01-11
forum: General Help
---

### Post by Norsk.Firefox on 2009-01-11
Hello
Is there any FTP client for Linux that chmod on upload?
Use gFTP now, but can't get it to chmode on upload. The one I have found with this function is the integrated FTP client in Aptana, but it's to buggy to be used.

Anyone?

---

### Post by blueridgedog on 2009-01-11
I know filezilla can chmod files, but I do not recall if it can do it automatically.

---

### Post by JasonInferno on 2009-11-03
Yeah, but unless you can link me otherwise, Filezilla only works on 64bit machines.
I'm in the same rut as the OP, so I'm also looking for a (32bit) FTP client that can ChMod files on the server.

---

### Post by blueridgedog on 2009-11-03
The first Linux link here:

[http://filezilla-project.org/download.php](http://filezilla-project.org/download.php)

is for 32 bit systems.  They call it i586, but that is just geekspeak for pentium class processors.

---

### Post by morningboat on 2009-11-03
If you try to seek the auto chmod during the upload, you can have a look at CrossFTP's advanced permission control function. At its Sites -> Site Manager -> Options -> Permission Inheritance, it can choose "from Parent" or "from Source (FXP)". Hence, I think you can choose the option of inheriting the permission from the parent folder. After setting up the top folder's permission, and all the transferred files will automatically be chmod.

---

