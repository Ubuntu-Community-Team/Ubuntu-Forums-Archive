---
title: "Thunar crash when I try to unpack a file (zip, tar, etc.)"
date: 2012-11-13
forum: Desktop Environments
---

### Post by cmolinap1 on 2012-11-13
Hi,
Thunar fails when I try to unpack a file using the option: Extract here ... When I use the Extract option in another folder sometimes fails.

Has anyone else experienced a similar situation?

Xubuntu 12.10, Thunar 1.5.2, Spanish language, Asus Eee PC 701SD, 8GB SSD, 1 GB RAM

cmolinap

---

### Post by badhorse on 2012-11-14
It's a file-roller bug:

[http://ubuntuforums.org/showthread.php?t=2072704]("http://ubuntuforums.org/showthread.php?t=2072704")

Here is the launchpad bug page:

[https://bugs.launchpad.net/ubuntu/+bug/978789]("https://bugs.launchpad.net/ubuntu/+bug/978789")

---

### Post by PerLowgren on 2012-12-04
I replaced file-roller with squeeze and it worked until I had to extract  a file-format unsupported by squeeze, so I found this alternative  solution: [http://askubuntu.com/questions/52965/thunar-archive-plugin-not-working](http://askubuntu.com/questions/52965/thunar-archive-plugin-not-working)

Edit the file _gnome-file-roller.tap_ which on my machine is located here:[INDENT] /usr/lib/x86_64-linux-gnu/thunar-archive-plugin/gnome-file-roller.tap
[/INDENT]Replace:
```
file-roller "--extract-to=$(pwd)" --extract-here --force "$@"
```With:
```
file-roller --extract-here --force "$@"
```

---

