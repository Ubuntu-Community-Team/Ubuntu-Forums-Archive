---
title: "Klamav Install"
date: 2006-01-27
forum: Desktop Environments
---

### Post by AlexanRO on 2006-01-27
I am attempting to install Klamav using the installer provided [http://sourceforge.net/project/showfiles.php?group_id=102171&package_id=109678]("http://sourceforge.net/project/showfiles.php?group_id=102171&package_id=109678") see screenshots [http://klamav.sourceforge.net/klamavwiki/index.php/Main_Page]("http://klamav.sourceforge.net/klamavwiki/index.php/Main_Page") . The install instructions are as follows:

==========================
Installation Instructions:

==========================



Do what the filename tells you!!



(e.g. sh ./DoubleClickOrExecuteMeToInstallKlamaAV-0.XX

or ./DoubleClickOrExecuteMeToInstallKlamaAV-0.XX)



Any problems with the install please mail: [email]klamav-users@lists.sourceforge.net[/email].


==========================

So of course I do just that, but only get as far as:

***** Dazuko

***** Running configure (./configure)...

checking host system type... Linux

checking for make utility... ok (make)

checking for C compiler... ok (cc)

kernel source in /lib/modules/2.6.12-1-386/build... no

kernel source in /usr/src/linux... no

error: kernel source files not found

***** Return value 1

I am unclear as to what the problem may be and need some direction. TIA for the assistance.

AlexanRO

---

### Post by kaamos on 2006-01-27
Try this
```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by AlexanRO on 2006-01-27
problem solved TY

AlexanRO\\:D/

---

### Post by dcstar on 2006-01-28
[QUOTE=AlexanRO]I am attempting to install Klamav using the installer provided [http://sourceforge.net/project/showfiles.php?group_id=102171&package_id=109678]("http://sourceforge.net/project/showfiles.php?group_id=102171&package_id=109678") ........[/QUOTE]
This has nothing to do with the problem, but wouldn't it be better to post KDE issues in the KDE desktop forum, and not the GNOME one?

[http://ubuntuforums.org/forumdisplay.php?f=106](http://ubuntuforums.org/forumdisplay.php?f=106)

---

