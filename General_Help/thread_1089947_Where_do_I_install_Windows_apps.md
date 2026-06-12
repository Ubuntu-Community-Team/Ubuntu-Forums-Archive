---
title: "Where do I install Windows apps?"
date: 2009-03-07
forum: General Help
---

### Post by haciendadad on 2009-03-07
Ok, I just learned that Wine allows Windows apps to be installed so I am trying to install a app and I am choosing the custom install option and I have to choose an installation directory, so where do I install this too?

Also, if you can shed some light on purposes for these directories too.

/etc
/var
/usr


Thanks

---

### Post by taurus on 2009-03-07
If you install it with wine, it should go in your own $HOME, ~/.wine/drive_c/Program Files.

---

### Post by amauk on 2009-03-07
Accept the default installation folder
(uaually C:\Program Files\...)

In wine, the C:\ drive is actually /home/$USERNAME/.wine/drive_c/
but all wine apps see it as C:\

---

### Post by ekaqu on 2009-03-07
> **haciendadad said:**
> 
Also, if you can shed some light on purposes for these directories too.

/etc
/var
/usr
Thanks

[http://everything2.com/e2node/Linux%2520filesystem%2520hierarchy](http://everything2.com/e2node/Linux%2520filesystem%2520hierarchy)

That website sums up the differnt folders well.

"/etc   Contains configuration files which are local to the
      machine.  Some larger software packages, like  X11,
      can  have  their  own  subdirectories  below  /etc.
      Site-wide configuration files may be placed here or
      in  /usr/etc.  Nevertheless, programs should always
      look for these files in /etc and you may have links
      for these files to /usr/etc.
"

"/var   This  directory  contains files which may change in
      size, such as spool and log files.
"

---

### Post by guywithcable on 2009-03-07
Windows apps expect drive letters, and since Linux doesn't use them, Wine has to compensate. C: in Wine is mapped to .wine/drive_c in your home folder.  Others are mapped to your CDROM and other disks. H: is mapped to your Linux home folder. Z: is mapped to the root directory (/).

If you ask me (and I'm sure your didn't), drive letters are stupid. They only cause problems. Moving disks around in Linux is rarely a problem, but in Windows, changing one drive letter can screw up any number of things. Sometimes even the whole system.

---

