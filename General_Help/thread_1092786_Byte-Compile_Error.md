---
title: "Byte-Compile Error"
date: 2009-03-10
forum: General Help
---

### Post by Alansri on 2009-03-10
Using fresh install of ubuntu 8.04 Desktop 32 
Any way to fix? It confuzzles me.

THank you.

emacs-install emacs-snapshot
install/auctex: Setting up for emacs-snapshot (log file: /usr/share/emacs-snapshot/site-lisp/auctex//CompilationLog)... emacs-install: /usr/lib/emacsen-common/packages/install/auctex emacs-snapshot emacs22 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 5.

And this is what generated the above
____________________________________________________________

Setting up emacs-snapshot (1:20080228-1ubuntu1) ...
Byte-compiling add-on packages, please wait... failed.

!! Byte-compilation for emacs-snapshot failed!
!! This indicates a bug in one of the add-on packages
!! installed on your system, or a bug in Emacs itself.
!! Please file a bug report against emacs-snapshot
!! and attach the file /tmp/emacs-snapshot.E23181
dpkg: error processing emacs-snapshot (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 emacs-snapshot
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

