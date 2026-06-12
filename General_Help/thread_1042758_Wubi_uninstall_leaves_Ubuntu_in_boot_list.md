---
title: "Wubi uninstall leaves Ubuntu in boot list"
date: 2009-01-17
forum: General Help
---

### Post by EpicDem on 2009-01-17
I used Wubi to install Ubuntu on my Windows Vista 64 bit computer.  Upon discovering that drivers for my graphics card did not exist I uninstalled...  sort of.
The uninstaller told me Ubuntu was removed, however the 30 GB of files were still in the C drive (manually removed, not a problem), and Ubuntu still appears in the Windows Boot list.

Searching around brought me to [this thread]("http://ubuntuforums.org/showthread.php?t=458727") where the problem magically resolved itself, which proved little use to me.

As in that post, the vista utilities do not show the defunct Ubuntu as existing, but the option still remains.

Any help?

---

### Post by surj08 on 2009-01-20
i would use eas1ybdc by neosmart to clear those up! its because vista is a homo!

or in xp goto start run "msconfig" without the quotes goto boot and select check boot paths

Hope i helped!

---

### Post by azmo35 on 2009-01-21
Go to boot.ini and delete ubuntu.

---

### Post by synapse13 on 2009-01-29
I second the post above about EasyBCD.  

I had a similar problem after uninstalling Ubuntu through Wubi.  I'm running Vista 64 bit, and after uninstall I had not regained my lost hard drive space and Ubuntu still appeared on the boot loader screen.

Manually delete the Ubuntu folder on your C drive, then go download EasyBCD (free download) to modify bcdedit.exe for you (this is the boot loader program in Vista).  EasyBCD does it way easier, through graphical means.  Remove the Ubuntu listing and you'll be back to where you began.  EasyBCD link:
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by EpicDem on 2009-02-05
yup, that worked perfectly.  thanks, all.

---

