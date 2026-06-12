---
title: "Custom built fglrx module causes error"
date: 2006-03-27
forum: Desktop Environments
---

### Post by kikkum on 2006-03-27
Hi,

I'm building a custom kernel with the *linux-source-2.6.12* package and I'm building the fglrx module together with it from the *fglrx-kernel-source* package. When these are installed and fglrx is activated I get a strange system halt when I want to reboot from X (gnome or gdm). The screen gets filled with random looking stripes in some colors and I can't do anything but use the power-button to turn it off (holding the button for 5 seconds).

To make the kernel and module packages I use the command

$ fakeroot make-kpkg --versionoptions --initrd kernel_image modules_image

There doesn't seem to be any problem, exept for the following during fglrx compilation:

```
/usr/bin/make clean SYSSRC=/usr/src/linux -C /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x -f Makefile EXTRAVERSION=.lappum-1.4
/bin/sh: -dumpversion: command not found
/bin/sh: -dumpversion: command not found
make[3]: Entering directory `/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x'
rm -f *.c *.h *.o *.ko *.GCC* .??*
rm: cannot remove `.tmp_versions': Is een map
make[3]: *** [clean] Fout 1
make[3]: Leaving directory `/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x'make[2]: *** [clean] Fout 2
make[2]: Leaving directory `/usr/src/modules/fglrx-kernel'
make[1]: *** [kdist_image] Fout 2
make[1]: Leaving directory `/usr/src/modules/fglrx-kernel'
Module /usr/src/modules/fglrx-kernel failed.
Hit return to Continue
```

In fact this shouldn't be a problem though, because it only fails in cleaning up; the .deb package has already been created.

I btw patched the source before compiling with the following file:

```
diff -ur fglrx-kernel.orig/debian/control.template fglrx-kernel/debian/control.template
--- fglrx-kernel.orig/debian/control.template	2005-02-08 14:12:16.000000000 +0300
+++ fglrx-kernel/debian/control.template	2005-02-09 04:12:46.846719876 +0300
@@ -8,7 +8,6 @@
 Package: fglrx-kernel-#KVERS#
 Architecture: i386
 Provides: fglrx-kernel-6.8.0-8.16.20
-Depends: fglrx-kernel-common (>= 6.8.0-8.16.20)
 Recommends: linux-image-#KVERS#
 Description: ATI binary kernel module for Linux #KVERS#
  These XFree86/X.Org 4.x binary drivers provide optimized hardware acceleration
diff -ur fglrx-kernel.orig/debian/dirs.template fglrx-kernel/debian/dirs.template
--- fglrx-kernel.orig/debian/dirs.template	2005-02-08 14:12:16.000000000 +0300
+++ fglrx-kernel/debian/dirs.template	2005-02-09 04:10:15.288156598 +0300
@@ -1,2 +1,2 @@
-lib/modules/#KVERS#/nvidia
+lib/modules/#KVERS#/fglrx
 usr/share/lintian/overrides
diff -ur fglrx-kernel.orig/debian/rules fglrx-kernel/debian/rules
--- fglrx-kernel.orig/debian/rules	2005-02-08 14:12:16.000000000 +0300
+++ fglrx-kernel/debian/rules	2005-02-09 04:08:13.836294392 +0300
@@ -73,10 +73,10 @@
 
 %.Makefile :
 	# select which makefile to use.
-	rm -f $(CURDIR)/$(dirname)/Makefile || true
-        cd $(CURDIR)/$(dirname) ; \
-	ln -s Makefile.kbuild Makefile ; \
-	cd .. ; \
+#	rm -f $(CURDIR)/$(dirname)/Makefile || true
+#	cd $(CURDIR)/$(dirname) ; \
+#	ln -s Makefile.kbuild Makefile ; \
+#	cd .. ; \
 
 
 .PHONY: configure configure-stamp
```

This patch is needed for it to compile at all. I got it from [http://ubuntuforums.org/showthread.php?t=11806](http://ubuntuforums.org/showthread.php?t=11806) and edited it for use with my version of the fglrx source package.

What can I do to make the error (striped screen and not being able to do anything) after shutting down from X go away?

---

### Post by kikkum on 2006-03-29
Bump :)

---

