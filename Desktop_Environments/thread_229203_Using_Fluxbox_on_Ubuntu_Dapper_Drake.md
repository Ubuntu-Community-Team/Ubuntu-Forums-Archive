---
title: "Using Fluxbox on Ubuntu Dapper Drake"
date: 2006-08-04
forum: Desktop Environments
---

### Post by gary201147 on 2006-08-04
Is there no version of Fluxbox that will work on Dapper? I tried installing Fluxbox fluxbox_0.9.15.1-1_i386.deb that was intended for Ubuntu Hoary and got the following msg

Selecting previously deselected package fluxbox.
(Reading database ... 105326 files and directories currently installed.)
Unpacking fluxbox (from fluxbox_0.9.15.1-1_i386.deb) ...
dpkg: dependency problems prevent configuration of fluxbox:
 fluxbox depends on menu (>= 2.1.19); however:
  Package menu is not installed.
 fluxbox depends on libimlib2; however:
  Package libimlib2 is not installed.
 fluxbox depends on libltdl3 (>= 1.5.2-2); however:
  Package libltdl3 is not installed.
dpkg: error processing fluxbox (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fluxbox

Im assuming it is looking for files in the kernel that no longer exist. Should i just wait for a release for Dapper?

---

### Post by herrpoon on 2006-08-04
Not too sure about the errors, but you could just compile it from source which is probably the better option regardless.  Try this: [http://www.ubuntuforums.org/showthread.php?t=116759](http://www.ubuntuforums.org/showthread.php?t=116759)

---

