---
title: "OpenGL broken after NVIDIA driver reinstall"
date: 2009-02-01
forum: General Help
---

### Post by jim.bauer10 on 2009-02-01
Hey everyone.
New to the forums, not so much to Ubuntu.
I've got what seems to be a pretty uncommon problem (or at least one for which the most common solutions don't work).  I attempted to install the newest set of NVIDIA proprietary drivers (180.22) for my 8500 GT yesterday using the official NVIDIA installer, but I did not know at the time that you had to disable a plugin or two and remove the current driver using Hardware Drivers before doing so.  After installation and a reboot, I was forced into the recovery console and an fsck.  That finished, and I decided that the 180.22 drivers must not be what I wanted and used Hardware Drivers to reinstall the old 177's.  Now everything works again except for OpenGL.  I've tried playing with the symlinks between the libraries because I read that that might be the problem, but to no avail.  No screensavers that use OpenGL work, Compiz tells me that xgl is not present, glxgears says something about a wrong ELF class (ELFCLASS32), and the OpenGL/GLX dialog in X Server Settings says "Fail to query the GLX server vendor".

I'll gladly provide whatever information you guys need to help me fix this.  Thanks in advance.

---

