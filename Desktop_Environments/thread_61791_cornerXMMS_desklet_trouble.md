---
title: "cornerXMMS desklet trouble"
date: 2005-09-02
forum: Desktop Environments
---

### Post by xmastree on 2005-09-02
I'm trying to install cornerXMMS but whatever version I download I get the same error:
```
Could not find sensor 'CornerXMMS'
A sensor could not be found. This usually means that it has not been installed.
```So where do I find this elusive sensor? It seems that the original version is the lower left, and the other two are modifications. With this in mind I first installed the original, expecting this sensor to be included with it. That fails the same way.

I looked around, and I found```
chris@ubuntu:~/.gdesklets/Sensors/CornerXMMS$ ls
__init__.py  __init__.pyc
```So it appears there's something there...

Any ideas why it won't work? The version I'm interested in is the [upper right one]("http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=228"), which at least says it needs the sensor.

Other desklets (FTB) are ok, so I think it's a cornerXMMS problem rather than a desklets problem.

---

### Post by xmastree on 2005-09-09
[COLOR=Red][SIZE=3]**Nobody?**[/SIZE][/COLOR]
It's one of the most downloaded ones, surely someone must have got it working... :neutral:

---

### Post by Eckdar on 2005-09-16
If you're still having this problem try installing first these two desklets: "xmms-2.tgz" (no corner version) and "xmmscorner.tar.gz". Maybe it will help.

---

