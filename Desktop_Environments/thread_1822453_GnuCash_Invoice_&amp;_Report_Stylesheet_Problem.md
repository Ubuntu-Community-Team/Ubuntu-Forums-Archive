---
title: "GnuCash Invoice &amp; Report Stylesheet Problem"
date: 2011-08-10
forum: Desktop Environments
---

### Post by concord on 2011-08-10
This header file no longer appears when it is set as the
"stylesheet/imags/heading banner"

Ubuntu 11.04
GnuCASH v.2.4.2 (from the ubuntu 11.04 repos)

This worked in GnuCASH Ubuntu 10.04 (gnucash 2.2.9-5) but no longer works after doing a clean install followed by copying ~/.gnucash and ~/.aqbanking back into place.

The rest of the attributes of both my custom Invoice & Report stylesheet still work (ie colours, etc.) but even when creating a brand new custom stylesheet I cannot get these images to appear after adding them to a stylesheet and saving the settings.  This worked fine in the previous version of the application.

I have tried deleting the old stylesheet(s) and recreating from scratch and the only thing that does not work is placing the banner or logo images where they are supposed to be.

I've done an strace to verify that the image is being found: it's just not appearing.

open("/home/concord/Artwork/gnucash_header.png", O_RDONLY) = 32
fstat(32, {st_mode=S_IFREG|0644, st_size=29049, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f243fc7c000
read(32, "\211PNG\r\n\32\n\0\0\0\rIHDR\0\0\3\261\0\0\0\354\10\6\0\0\0\242\333!"..., 65536) = 29049
read(32, "", 32768)                     = 0
close(32)                               = 0

I have asked around on IRC (irc.gnome.org #gnucash) and it was suggested that it might be a webkit issue, libwebkitgtk is verified as installed.  Any help appreciated.

- Frank

---

### Post by concord on 2011-08-10
This issue is solved.  Version 2.4.2 that ships with Ubuntu 11.04 is broken.  Upgrading to GnuCash 2.4.7 fixed this problem for me.

See this page for the solution:

[https://bugzilla.gnome.org/show_bug.cgi?id=648209](https://bugzilla.gnome.org/show_bug.cgi?id=648209)

---

