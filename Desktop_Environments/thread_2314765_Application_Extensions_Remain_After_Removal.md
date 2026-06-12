---
title: "Application Extensions Remain After Removal"
date: 2016-02-23
forum: Desktop Environments
---

### Post by 12 leaders on 2016-02-23
Hello,

I've been having a bit of trouble removing old icons and extensions from Ubuntu after the removal of applications. For instance, although I removed PlayOnLinux, MS Word's icon still remains in my menus. Another example: after removing Canon packages, the icons still remain in Nautilus (please see attached photo).

I personally like to keep a clean desktop environment. Is there any way to remove these old extensions?

Thanks.

[IMG]http://i64.tinypic.com/3008ykp.png[/IMG]

---

### Post by sandyd on 2016-02-23
Moved to *Desktop Environments*
Try checking if the .desktop file for the application has been removed from /usr/share/applications, and ~/.local/share/applications

---

### Post by kostkon on 2016-02-23
Running
```
sudo apt-get autoremove
```
wouldn't harm either, you may still got some left-over packages from your previous installations.

---

