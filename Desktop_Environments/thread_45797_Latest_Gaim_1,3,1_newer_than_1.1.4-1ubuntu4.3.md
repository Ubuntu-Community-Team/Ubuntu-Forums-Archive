---
title: "Latest Gaim 1,3,1 newer than 1.1.4-1ubuntu4.3"
date: 2005-07-01
forum: Desktop Environments
---

### Post by jkrolen5500 on 2005-07-01
Why is the ubuntu gaim so far out of date?  I wan't to run the newest Gaim 1.3.1 but I get the following errors during ./configure

checking for silcclient... Package silcclient was not found in the pkg-config search path.
Perhaps you should add the directory containing `silcclient.pc'
to the PKG_CONFIG_PATH environment variable
No package 'silcclient' found
checking for silc... Package silc was not found in the pkg-config search path.
Perhaps you should add the directory containing `silc.pc'
to the PKG_CONFIG_PATH environment variable
No package 'silc' found


Checking for GLIB - version >= 2.0.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occurred. This usually means GLIB is incorrectly installed.
configure: error:
*** GLib 2.0 is required to build Gaim; please make sure you have the GLib
*** development headers installed. The latest version of GLib is
*** always available at [http://www.gtk.org/](http://www.gtk.org/).



But 

root@laptop:/home/jer/gaim-1.3.1 # apt-get install libglib2.0-0
Reading package lists... Done
Building dependency tree... Done
libglib2.0-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


So its installed and I am stuck with an older version of Gaim :(

---

### Post by NeoChaosX on 2005-07-01
Have you added the [Ubuntu Backports](http://backports.ubuntuforums.org)  repos to your apt list? It includes Gaim 1.3.1 for Hoary.

---

### Post by byen on 2005-07-01
[QUOTE=NeoChaosX]Have you added the [Ubuntu Backports](http://backports.ubuntuforums.org)  repos to your apt list? It includes Gaim 1.3.1 for Hoary.[/QUOTE]
 yup. its already in there.. you just gotta update it. wonder why Ubuntu never updates its release on a time to time basis is a wonder to me. Infact in many sites this has been the only complaint people seem to have with ubuntu. Well ..cant say much about it cuz i know the guys are tryin their best. Oh well!

---

### Post by jkrolen5500 on 2005-07-01
Thank ye!

---

### Post by christooss on 2005-07-01
You have to add backport staging I think.

---

### Post by N'Jal on 2005-07-01
Just use the autopackage gaim, since it's autopackaged the day it's realeased and your not left waiting for a few weeks for it to be backported. Once it is then upgrade but the more i play with autopackage the more i like it, though to install something system wide you have to enable the root account.

If none of that made sense i will explain it later.

---

