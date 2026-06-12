---
title: "Apt errors on libgtk2.0-bin"
date: 2006-06-30
forum: Desktop Environments
---

### Post by soce_32 on 2006-06-30
After a recent upgrade, every time I run aptitude, dpkg, synaptic, and such, I get this error:

Setting up libgtk2.0-bin (2.8.18-0ubuntu2) ...
Updating the IM modules list for GTK+-2.4.0...done.
Updating the gdk-pixbuf loaders list for GTK+-2.4.0.../usr/sbin/update-gdkpixbuf-loaders: line 25: 28595 Segmentation fault      /usr/bin/gdk-pixbuf-query-loaders >$TMPFILE
dpkg: error processing libgtk2.0-bin (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 libgtk2.0-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up libgtk2.0-bin (2.8.18-0ubuntu2) ...
Updating the IM modules list for GTK+-2.4.0...done.
Updating the gdk-pixbuf loaders list for GTK+-2.4.0.../usr/sbin/update-gdkpixbuf-loaders: line 25: 28616 Segmentation fault      /usr/bin/gdk-pixbuf-query-loaders >$TMPFILE
dpkg: error processing libgtk2.0-bin (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 libgtk2.0-bin

I have tried reinstalling, purging and installing fresh, gdb backtraces on update-gdkpixbuf-loaders point to libc6 and libc6-i686, so I have reinstalled both of thos packages, but I simply cannot get rid of this error.

It does not affect my system as far as I can tell, but it is annoying to have to see it on every update and package install.

Can anyone suggest some other things to try?

Thanks

---

