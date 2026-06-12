---
title: "Black menus bug with gtk-qt-engine."
date: 2005-12-20
forum: General Help
---

### Post by Junx on 2005-12-20
(original post at [http://www.kubuntuforums.net/forums/index.php?topic=2388.0](http://www.kubuntuforums.net/forums/index.php?topic=2388.0))

Any version of gtk2-engines-gtk-qt on both the Ubuntu and Debian repositories will cause menus to have a black background with black text.  The typical warning given by STDERR is "Gdk-WARNING **: gdk_window_set_back_pixmap(): pixmap must have a colormap".  This problem seems to exist on any version of GTK/GDK starting from 2.8 and above.  Someone has posted a patch on kde-look.org, and I've also emailed the debian-qt mailing list, but no actual patched versions of the GTK-Qt engine are available, and I can't get the damn thing to compile for the life of me.

Anyone have any suggestions?  Is it possible for Kubuntu to release a patched version of gtk2-engines-gtk-qt?

--------BEGIN PATCH--------
diff -urN gtk-qt-engine-0.6.orig/src/qt_theme_draw.c
gtk-qt-engine-0.6/src/qt_theme_draw.c
--- gtk-qt-engine-0.6.orig/src/qt_theme_draw.c 2004-12-21 21:28:34 +0600
+++ gtk-qt-engine-0.6/src/qt_theme_draw.c 2005-09-30 08:20:50 +0700
@@ -1777,6 +1777,7 @@
{
pixmap = pix_test;
parent_relative = FALSE;
+ gdk_drawable_set_colormap(pixmap, style->colormap);
}

gdk_window_set_back_pixmap (window, pixmap, parent_relative);
---------END PATCH---------

---

### Post by One Quick Question on 2005-12-20
Taken from [this post](http://www.ubuntuforums.org/showthread.php?t=101097), try this:
```

sudo apt-get build-dep gtk2-engines-gtk-qt
sudo apt-get source gtk2-engines-gtk-qt
(apply the patch)
sudo dpkg-buildpackage -rfakeroot -uc -b  (in the gtk2-engines-gtk-qt directory)
sudo dpkg -i gtk2-engines-gtk-qt

```

Does that do anything useful?

---

### Post by Junx on 2005-12-20
I think so.  Gtk-qt has been the only program that didn't want to be compiled manually by me in the past few months, so I knew there had to be some easier way.

Edit: yep, it worked! :)

---

