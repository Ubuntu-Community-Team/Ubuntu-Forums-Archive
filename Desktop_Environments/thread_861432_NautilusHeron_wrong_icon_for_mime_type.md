---
title: "Nautilus/Heron: wrong icon for mime type"
date: 2008-07-16
forum: Desktop Environments
---

### Post by michaelbrewerdavis on 2008-07-16
I know there have been threads on this before, and bugs reported, but I haven't found any resolution.  I have a custom mimetype/icon pair that gets displayed correctly by most programs, but for which the default icon is used in nautilus.

Ubuntu 8.04 with all default updates applied
nautilus 2.22.3

mime type: 
application/t4l-pixie (assoc. to .pxi and .PXI)
icons placed at both:
/usr/share/icons/hicolor/48x48/mimetypes/application-t4l-pixie.png /usr/share/icons/hicolor/48x48/mimetypes/gnome-mime-application-t4l-pixie.png

I use xdg-mime install and xdg-icon-resource-install for these.

When viewed within Nautilus (either on the desktop or in a window), I am shown the default icon.  When viewed using Firefox's file dialog, or through other apps which access icons via gtk and gnome libraries, the icon is correct.

Anyone have a lead on this?

Thanks much,
Michael

---

### Post by michaelbrewerdavis on 2008-09-30
Resolved the issue by adding my icons to the 'gnome' theme as well as 'hicolor':

[http://www.mail-archive.com/nautilus-list@gnome.org/msg05238.html](http://www.mail-archive.com/nautilus-list@gnome.org/msg05238.html)

---

