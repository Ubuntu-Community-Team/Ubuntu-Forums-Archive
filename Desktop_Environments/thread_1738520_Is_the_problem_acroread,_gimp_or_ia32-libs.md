---
title: "Is the problem acroread, gimp or ia32-libs?"
date: 2011-04-24
forum: Desktop Environments
---

### Post by hongguang.cui on 2011-04-24
Hi, all
I use normally acroread to snapshot image in the PDF files to paste gimp on the Ubuntu 10.10 (version of ia32-libs is ubuntu9). Now, under ubuntu 11.04 (ia32-libs is ubuntu13), I can't use acroread to snapshot any image in the PDF files to paste gimp. The message of gimp is "There is no image data in the clipboard to paste." But now, I open libreoffice and paste, the image from acroread is appear. And I mark the image in the libreoffice, and I can paste normally in gimp.
This is the message of acroread startup:
```

(acroread:3039): GdkPixbuf-WARNING **: Error loading XPM image loader: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so: wrong ELF class: ELFCLASS64

(acroread:3039): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
(acroread:3039): Gdk-CRITICAL **: IA__gdk_window_set_icon_list: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(acroread:3039): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

....

```
and my kernel is
```

2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```
I used apt-get install acroread.

Any Help?
Thanks!

---

### Post by ponsfrilus on 2011-04-29
Same here. Please help.

---

### Post by starNIX on 2011-05-03
I've got the same problem with putty on 64bit Natty.

---

### Post by mörgæs on 2011-05-04
Are these problems for an upgraded 11.04 or a fresh install?

---

### Post by starNIX on 2011-05-04
> **mörgæs said:**
> Are these problems for an upgraded 11.04 or a fresh install?

Mine is upgraded from 10.10..

On my fresh install at home putty works fine.

---

### Post by mörgæs on 2011-05-04
Then I guess you know the solution... :-)

---

### Post by starNIX on 2011-05-04
Reinstalling from scratch is not the answer.  This is my work PC.  I cannot be down for that long.  There has to be something else going on here.

---

### Post by mörgæs on 2011-05-04
If it is a work PC, I would definitely reinstall rather than trying to troubleshoot.

---

### Post by starNIX on 2011-05-04
Well it isn't really a show-stopper since the windows version of putty works just fine.  Just a little annoying.

---

