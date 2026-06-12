---
title: "Katalog  Anyone tried to load this program?"
date: 2006-06-25
forum: Desktop Environments
---

### Post by interse on 2006-06-25
I have tried to download this program using Synaptic Package Manager.  After I 'successfully' download this program, I am unable to find it on my system.  It certainly is not installed.  

Anyone else had this experience?  In the Package Manager it shows up as version 0.3, which I know is not the most recent, but it is for ubuntu.   It does not install for me and I cannot find it when I search my files.   I do find 'katalog.desktop' which appars to be an install script.

---

### Post by aysiu on 2006-06-25
What happens when you press Alt-F2 and type ```
katalog
```? **Edit**: Wait... have you installed it yet or not?

I just tried installing and using *katalog*. As far as I can tell... it can't be run!

---

### Post by interse on 2006-06-25
In tried to run katalog in a terminal.  No success.
I have uninstalled it.   

But I really would like to install it.  I have access to version 0.4 on a disk, but I am curious as to why version 0.3 in the repository can't be run.

---

### Post by aysiu on 2006-06-25
I don't know. I tried just about every which way.

---

### Post by interse on 2006-06-25
I guess there is some satisfaction in knowing that it isn't me!
Thanks for your efforts.  

I will try to install the program from the latest disk from Linux Format.

---

### Post by interse on 2006-06-27
Has anyone downloaded and installed this program, from the repositories, successfully?

I have used Synaptic to get this program, but there is no indication that it has installed.

---

### Post by aysiu on 2006-06-27
Well, I got indications that it was installed, but I was unable to actually *run* the program.

---

### Post by interse on 2006-06-28
Yes, I got the same: indication that Katalog was installed.  But calling for it from the terminal produced nothing.  I 'installed' the next version, 0.4, from a CD from Linux Format (tar file) and the same thing happened.  Lots of files and when compiled, it produced quite a few Preview-Katalog files, but that was it.  Attempts to make-install, etc. produced nothing.  

Could it be that it REQUIRES a KDE setup?   

Next question, is there some other program which does the same thing; catalogues CDs, etc?

---

### Post by marwal on 2006-06-28
installed via synaptic

> /.
/usr
/usr/lib
/usr/lib/libkatalog.so.0.0.0
/usr/lib/libkatalog.la
/usr/lib/kde3
/usr/lib/kde3/kio_katalogslave.so
/usr/lib/kde3/kio_katalogslave.la
/usr/lib/kde3/kfile_katalog.so
/usr/lib/kde3/kfile_katalog.la
/usr/share
/usr/share/icons
/usr/share/icons/crystalsvg
/usr/share/icons/crystalsvg/48x48
/usr/share/icons/crystalsvg/48x48/mimetypes
/usr/share/icons/crystalsvg/48x48/mimetypes/katalogfolder.png
/usr/share/icons/crystalsvg/48x48/mimetypes/katalogitem.png
/usr/share/icons/crystalsvg/48x48/mimetypes/katalog.png
/usr/share/icons/crystalsvg/16x16
/usr/share/icons/crystalsvg/16x16/mimetypes
/usr/share/icons/crystalsvg/16x16/mimetypes/katalog.png
/usr/share/icons/crystalsvg/16x16/mimetypes/katalogfolder.png
/usr/share/icons/crystalsvg/16x16/mimetypes/katalogitem.png
/usr/share/icons/crystalsvg/64x64
/usr/share/icons/crystalsvg/64x64/mimetypes
/usr/share/icons/crystalsvg/64x64/mimetypes/katalog.png
/usr/share/icons/crystalsvg/64x64/mimetypes/katalogitem.png
/usr/share/icons/crystalsvg/64x64/mimetypes/katalogfolder.png
/usr/share/icons/crystalsvg/32x32
/usr/share/icons/crystalsvg/32x32/mimetypes
/usr/share/icons/crystalsvg/32x32/mimetypes/katalog.png
/usr/share/icons/crystalsvg/32x32/mimetypes/katalogitem.png
/usr/share/icons/crystalsvg/32x32/mimetypes/katalogfolder.png
/usr/share/icons/crystalsvg/22x22
/usr/share/icons/crystalsvg/22x22/mimetypes
/usr/share/icons/crystalsvg/22x22/mimetypes/katalogfolder.png
/usr/share/icons/crystalsvg/22x22/mimetypes/katalogitem.png
/usr/share/icons/crystalsvg/22x22/mimetypes/katalog.png
/usr/share/mimelnk
/usr/share/mimelnk/application
/usr/share/mimelnk/application/x-katalog.desktop
/usr/share/mimelnk/application/x-katalogitem.desktop
/usr/share/mimelnk/inode
/usr/share/mimelnk/inode/katalog-directory.desktop
/usr/share/services
/usr/share/services/katalogslave.protocol
/usr/share/services/kfile_katalog.desktop
/usr/share/services/katalogdcop.desktop
/usr/share/apps
/usr/share/apps/konqueror
/usr/share/apps/konqueror/servicemenus
/usr/share/apps/konqueror/servicemenus/katalog.desktop
/usr/share/applications
/usr/share/applications/kde
/usr/share/applications/kde/katalog.desktop
/usr/share/doc
/usr/share/doc/katalog
/usr/share/doc/katalog/README
/usr/share/doc/katalog/TODO
/usr/share/doc/katalog/AUTHORS
/usr/share/doc/katalog/copyright
/usr/share/doc/katalog/changelog.gz
/usr/share/doc/katalog/NEWS.gz
/usr/share/doc/katalog/changelog.Debian.gz
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/katalog
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/katalogservice.1.gz
/usr/share/man/man1/katalog.1.gz
/usr/share/man/man1/katalogdcop.1.gz
/usr/bin
/usr/bin/katalogservice
/usr/bin/katalogdcop
/usr/include
/usr/include/kde
/usr/include/kde/katalogdcopinterface.h
/usr/lib/libkatalog.so.0
/usr/lib/libkatalog.so
/usr/share/doc/katalog/html

so katalogservice and katalogdcop is the binary files

---

### Post by interse on 2006-06-28
Unclear.   Does the program work?  Is the command, in terminal, katalogservice or katalogdcop, to start the program?   

Two of us, aysiu and interse, have not been able to get the program to run.

---

### Post by aysiu on 2006-06-28
I tried everything in /usr/bin, and to no avail. The *man* page was no help, and the help didn't work, either.

---

### Post by Witty Name on 2006-07-21
It worked for me after a reboot.

---

