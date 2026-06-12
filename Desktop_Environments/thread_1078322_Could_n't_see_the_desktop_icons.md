---
title: "Could n't see the desktop icons ??"
date: 2009-02-23
forum: Desktop Environments
---

### Post by chinmaya_n on 2009-02-23
I could not see the desktop icons ......... To bring them back I'm using the following commands: (I dont know what those commands mean actually.... I saw them in some other threads)

```
$ gconftool-2 --recursive-unset /apps/nautilus/desktop

$ gconftool-2 --recursive-unset /apps/nautilus
```
But for the next boot they r not coming !!?? 
This happend after my experiment,  written clearly in this thread:
[http://ubuntuforums.org/showthread.php?t=1073456](http://ubuntuforums.org/showthread.php?t=1073456)

Plz help me !!:(

---

### Post by x33a on 2009-02-25
try, alt+f2, gconf-editor.

then, apps -> nautilus -> desktop -> volumes visible.

apps -> nautilus -> preferences -> show desktop.

---

