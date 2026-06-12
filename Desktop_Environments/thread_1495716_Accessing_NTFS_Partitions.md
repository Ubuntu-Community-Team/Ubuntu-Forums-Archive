---
title: "Accessing NTFS Partitions"
date: 2010-05-28
forum: Desktop Environments
---

### Post by javarunner on 2010-05-28
I've recently installed Ubuntu 10.0.4 on a Win 7 PC and now have a dual-boot box. I need to know how to make various resources stored in the Win 7 world (ie; NTFS) available to several Ubuntu-based apps. Example, how to make JAR files referenced as libraries in Eclipse IDE in Win 7 available to a separate Eclipse instance running in Ubuntu.  I could download these JARs into the Ubuntu system but don't really want to do that, unless necessary. There has to be a way.
Any ideas very welcome.
:confused:

---

### Post by WinRiddance on 2010-05-28
> **javarunner said:**
> I've recently installed Ubuntu 10.0.4 on a Win 7 PC and now have a dual-boot box. I need to know how to make various resources stored in the Win 7 world (ie; NTFS) available to several Ubuntu-based apps. Example, how to make JAR files referenced as libraries in Eclipse IDE in Win 7 available to a separate Eclipse instance running in Ubuntu.  I could download these JARs into the Ubuntu system but don't really want to do that, unless necessary. There has to be a way.
Any ideas very welcome.
:confused:

I don't quite follow your question but there are some things, **particularily working Windows apps.** that are never supposed to be "used" as applications within a raw Ubuntu environment unless you're going either through Wine or a Virtual box (both available from the software center). The Nautilus file manager (start ---> places ---> computer) should provide you with access to all of the contents of an entire NTFS partition _simply by clicking on it_ which will automatically cause the NTFS partition to become mounted i.e. useable. I'm assuming of course that you're the administrator/owner of the machine with both Operating Systems ....

Ooops, forgot to mention that you can also create bookmarks in Nautilus to any folder on the machine. Those bookmarks will appear at the lower left of Nautilus where Documents, Pictures, Music, and so on are located ... meaning that you can access your Win7 environment, locate folders there, and then create instant bookmarks to those folders in your file manager. But if you're going to do that ... **why not just toss Win7 altogether** ??? (rhetorical question, no answer required)

---

### Post by javarunner on 2010-05-28
Thanks - I'll give Nautilus a try.

---

### Post by mechanic on 2010-05-29
One thing as far as NTFS resources goes, Ubuntu still has problems writing to  NTFS partitions. You may need to install ntfs-3g and then ensure /sbin/mount.ntfs points to /sbin/mount.ntfs-3g. On my last install of Lucid this symlink was in place after I installed the ntfs-3g driver. Why these simple things can't be sorted out quickly, goodness knows!

---

