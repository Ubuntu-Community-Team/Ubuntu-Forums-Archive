---
title: "[SOLVED] E17 error message"
date: 2007-10-13
forum: Desktop Environments
---

### Post by corney91 on 2007-10-13
Hi,
I've been using E17 for a couple of weeks now and really enjoying it, but recently I've been getting an error message saying the session lasted less than 10 seconds, there's something wrong. And in .xsession-errors:
> 
(process:7667): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:7671): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
/etc/X11/Xsession.d/40guidance-displayconfig_restore: 11: /usr/bin/displayconfig-restore: not found
enlightenment: error while loading shared libraries: libcurl.so.4: cannot open shared object file: No such file or directory

Any ideas on how to get it working again? Any help appreciated.


EDIT: Never mind. Solved it (I should have been paying more attention):
```
install libcurl3-dev
```

---

