---
title: "Wrong or missing icons for libreoffice in cinnamon taskbar"
date: 2012-12-13
forum: Desktop Environments
---

### Post by xtrailrunner on 2012-12-13
I'm using Ubuntu 12.10 with cinnamon 1.6.7 and libreoffice 3.6.4.3.
When launching a program of the suite in some reproducible cases no icon or the wrong icon is displayed in the taskbar.
Examples:
 Running a .doc document with writer the icon of impress is displayed.
Running a .xls document with calc the icon of writer is displayed.
Sometimes there is also no icon at all.

Any help is appreciated because this is really confusing.

---

### Post by xtrailrunner on 2012-12-14
Interesting observation:
If I move the running LO application to another workspace the icon will be corrected. If I move the LO application back to the original workspace the icon stays correct.
That's a nice workaround ;)

---

### Post by xtrailrunner on 2013-03-16
Seems to be related with this:
[https://github.com/linuxmint/Cinnamon/commit/c0e37556e41026f952af5714611fccab73e1a079](https://github.com/linuxmint/Cinnamon/commit/c0e37556e41026f952af5714611fccab73e1a079)
Copied windowList.js to /usr/share/cinnamon/js/ui but without effect.

---

