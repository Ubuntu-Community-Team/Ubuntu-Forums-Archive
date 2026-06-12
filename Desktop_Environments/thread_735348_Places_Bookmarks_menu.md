---
title: "Places Bookmarks menu"
date: 2008-03-25
forum: Desktop Environments
---

### Post by zfreak7c5 on 2008-03-25
Is there a way to get the bookmarks in the places menu in Gnome to not turn into a sub menu when a certain number is reached.  I do not want to recompile Gnome as it says to do [[COLOR="Red"]here[/COLOR]]("http://gnomesupport.org/forums/viewtopic.php?t=12700"). 

            Thanks,

---

### Post by mssever on 2008-03-26
Actually, according to that thread, you don't have to recompile Gnome; you only have to recompile gnome-panel. While that thread is a year old, it's unlikely that the situation has changed any. Probably the only way is to recompile.

---

### Post by AbtZ on 2008-04-23
OK, how do I compile gnome-panel successfully?

I downloaded the source but after running ./configure it stops dead with error message

```
checking for PANEL... configure: error: Package requirements (ORBit-2.0 >= 2.4.0 gdk-pixbuf-2.0 >= 2.7.1 pango >= 1.15.4 gtk+-2.0 >= 2.11.3 glib-2.0 >= 2.15.6 gio-2.0 >= 2.15.6 libgnome-2.0 >= 2.13.0 libgnomeui-2.0 >= 2.5.4 libbonoboui-2.0 >= 2.1.1 gnome-desktop-2.0 >= 2.11.1 libglade-2.0 >= 2.5.0 gconf-2.0 >= 2.6.1 libgnome-menu >= 2.11.1 dbus-glib-1 >= 0.60) were not met:

No package 'ORBit-2.0' found
No package 'gdk-pixbuf-2.0' found
No package 'gtk+-2.0' found
No package 'libgnome-2.0' found
No package 'libgnomeui-2.0' found
No package 'libbonoboui-2.0' found
No package 'gnome-desktop-2.0' found
No package 'libglade-2.0' found
No package 'gconf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PANEL_CFLAGS
and PANEL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

As far as I can tell in Synaptic, these packages do not exist. Furthermore, manually searching for these is a bit cumbersome -- is there no automated way to do it?

Thanks.

---

### Post by mssever on 2008-04-23
> **AbtZ said:**
> OK, how do I compile gnome-panel successfully?

I downloaded the source but after running ./configure it stops dead. . . .

As far as I can tell in Synaptic, these packages do not exist. Furthermore, manually searching for these is a bit cumbersome -- is there no automated way to do it?

The libs exist, but they might be named differently. If you use pbuilder, it will take care of dependencies automatically. Get the Ubuntu source package (add the appropriate deb-src line to your sources.list, then sudo aptitude update && apt-get source gnome-panel (or whatever the source package is called). Modify the source as appropriate, and bump up the version number in debian/changelog (add ~yourname1). Build a source package using debuild -S then use pbuilder to make the .deb. Instructions are in this thread: [http://ubuntuforums.org/showthread.php?t=206382](http://ubuntuforums.org/showthread.php?t=206382)

---

### Post by tagno25 on 2008-05-01
Every time I run `debuild -S`, I receive the following error
```
dpkg-source: building gnome-panel in gnome-panel_2.22.1.2-0ubuntu3~tagno251.dsc
 dpkg-genchanges -S
dpkg-genchanges: not including original source code in upload
dpkg-buildpackage (debuild emulation): source only, diff-only upload (original source NOT included)
Now signing changes and any dsc files...
 signfile gnome-panel_2.22.1.2-0ubuntu3~tagno251.dsc Sebastien Bacher <seb128@canonical.com>
gpg: skipped "Sebastien Bacher <seb128@canonical.com>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available
debsign: gpg error occurred!  Aborting....
debuild: fatal error at line 1174:
running debsign failed

```
how do I get past that?

---

