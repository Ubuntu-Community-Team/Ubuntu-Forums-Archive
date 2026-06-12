---
title: "[SOLVED] tsclient custom screen size"
date: 2008-01-28
forum: Desktop Environments
---

### Post by starfry on 2008-01-28
Hello, I would like to get tsclient to run in a window (i.e. not full screen) but at a larger resolution than  the maximum available in the "use specified screen size" dropdown of 1400x1050.

Is there a config file I can edit to allow a custom size (like 1920x1200) ?

Thanks!

---

### Post by bloodniece on 2008-01-29
Try rdesktop since tsclient is more of a gui app and rdesktop is command line and more powerful.

here us how I run rdesktop from a lot of my workstation

```
rdesktop -g 1152x1024 -a 24 termserv
```

-g is geometry and can be any resolution
-a is color depth
try from terminal
```
man rdesktop
```
There are a ton more options with printers and redirected drivers. I found the best way to redirect drivers is to just share them via samba and map them to a drive letter once your in Windows.

---

### Post by starfry on 2008-02-02
Perfect, thanks for the solution :)

---

