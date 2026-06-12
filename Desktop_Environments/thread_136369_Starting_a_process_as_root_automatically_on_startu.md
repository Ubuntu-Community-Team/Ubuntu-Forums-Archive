---
title: "Starting a process as root automatically on startup"
date: 2006-02-25
forum: Desktop Environments
---

### Post by ravalox on 2006-02-25
Hi, I am looking to have mythbackend start when my machine does.  Coming from the gentoo world rc-update was what we used to do that, but Ubuntu must use something else; what is it?

---

### Post by Xian on 2006-02-25
To remove a service:
$ sudo update-rc.d <program> remove

To turn it back on:
$ sudo update-rc.d <program> defaults

---

### Post by ravalox on 2006-02-26
This isn't quite the answer I need, I need to run hdparm -d1 on a drive on startup; as well as kick off mythbackend as root on startup.

---

