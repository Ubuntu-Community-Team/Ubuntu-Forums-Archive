---
title: "Acrobat 9 acroread libqtcurve.so ELFCLASS64 (solved)"
date: 2010-02-28
forum: Desktop Environments
---

### Post by wd5gnr on 2010-02-28
Just fixed something that has been bugging me and thought it might help some one else.

In Kubuntu, I had a previously working acroread (Acrobat 9) that seemed to suddenly quit working. I don't run it much so whatever I did to break it wasn't apparent.

The message when running acroread from the terminal was:

```
(acroread:27538): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtcurve.so: wrong ELF class: ELFCLASS64

(acroread:27538): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtcurve.so: wrong ELF class: ELFCLASS64
```



So I realized that there was no 32 bit qtcurve theme and then I remembered that in System Settings, Appearance there is a GTK+ Appearance icon. In there the Widget style was set to QtCurve. Changing the style to Raleigh (the only other choice) got it working.

Yeah, yeah. I know. There are other PDF readers, etc. etc. But I thought someone might find this useful.

---

### Post by gatman3 on 2010-04-06
Wonderful!  Worked for me too. :guitar:

Initially I had no joy with your suggestion, but it looks like the reason was that I had a few pdf documents already open in firefox using the acrobat plugin.  Once I closed firefox and tried again it worked like a champ.

Thanks for posting this solution.

---

### Post by davemc on 2011-02-13
google chrome generates the same warning in Lucid Kubuntu AMD64.
```

(npviewer.bin:16524): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtcurve.so: wrong ELF class: ELFCLASS64

```

---

