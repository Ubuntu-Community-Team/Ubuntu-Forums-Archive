---
title: "Xubuntu 18.10 gtkrc-2.0 file doesn't work"
date: 2018-11-26
forum: Desktop Environments
---

### Post by rattskjelke on 2018-11-26
I installed Xubuntu 18.10 (replaced 18.04.1 LTS) and it looks like my *~/.gtkrc-2.0* file has no effect now.
Specifically *XfdesktopIconView::ellipsize-icon-labels = 0* no longer works.
Icon labels with long file names are truncated. Can anybody else confirm this or know how to fix it?

---

### Post by ajgreeny on 2018-11-26
I think those sort of configurations that used to be sorted in the ~/.gtkrc-2.0 file are now dealt with files that sit in ~/.config/gtk-3.0 though I have never made use of any of them to change anything on my system.

Make a search to see what you can find out about the **gtk.css** and **settings.ini** files if you have them in that folder.

Sorry I can't help more.

---

### Post by rattskjelke on 2018-11-26
> **ajgreeny said:**
> Make a search to see what you can find out about the **gtk.css** and **settings.ini** files if you have them in that folder.
I don't have those. On my installation the gtk-3.0 folder only has a *bookmarks* file.
I tried moving my .gtkrc-2.0 file there. That didn't help.
I tried renaming it several times to gtkrc-2.0, gtkrc-3.0, gtk.css, settings.ini, logging out and back in after each change, and none of those worked.
I think I will have to go back to 18.04.

Another thing I tried was going to the Xfce Settings Editor and under *xfce4-desktop/desktop-icons/* I made a new entry *ellipsize-icon-labels* and set it to *false*. That doesn't work either.

---

### Post by rattskjelke on 2018-11-26
I fixed it. Found the answer here
[https://forum.xfce.org/viewtopic.php?id=11878](https://forum.xfce.org/viewtopic.php?id=11878)

I created the file *~/.config/gtk-3.0/gtk.css* that contains:
```

* {
   -XfdesktopIconView-ellipsize-icon-labels: 0;
}

```

---

