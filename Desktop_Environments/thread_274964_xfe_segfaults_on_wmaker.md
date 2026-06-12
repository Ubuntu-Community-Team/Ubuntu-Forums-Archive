---
title: "xfe segfaults on wmaker"
date: 2006-10-10
forum: Desktop Environments
---

### Post by streeto on 2006-10-10
xfe segfaults when dragging files, using window maker. The problem does not occur when using Gnome.

Dragging files inside the panel works. When I drag something to the directory treeview, the program segfaults.

Version information:

Ubuntu 6.06.1 LTS
wmaker 0.92.0-5
xfe 0.84-4

Am I the last one on Earth using window maker? :???:

---

### Post by streeto on 2006-10-11
Installing version 0.88-1 of xfe, from [their project site]("http://sourceforge.net/projects/xfe"), solved the problem. Please note that this is an unnofficial .deb package, and I don't think it is even suitable for Ubuntu. But, it works, at least for now.

If I run into consistency problems in apt database, I'll post a comment here.

---

