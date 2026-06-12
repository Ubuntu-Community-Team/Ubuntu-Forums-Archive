---
title: "cdrom auto mount problem"
date: 2006-02-05
forum: Desktop Environments
---

### Post by gormine on 2006-02-05
When I insert a dvd and it automounts, the data is a bunch of symbols (invalid encoding). If I mount it manually with this command "sudo mount -t auto /dev/hdd /media/cdrom0", it works perfectly.

---

### Post by gormine on 2006-02-05
Apparently I fixed this by replacing the default "/dev/hdd	/media/cdrom0	udf,iso9660 user,noauto 0 0" with "/dev/hdd	"/media/cdrom0	auto	user	0	0"

I have to wonder, what is the noauto option for?

---

### Post by dcstar on 2006-02-05
[QUOTE=gormine]Apparently I fixed this by replacing the default "/dev/hdd	/media/cdrom0	udf,iso9660 user,noauto 0 0" with "/dev/hdd	"/media/cdrom0	auto	user	0	0"

I have to wonder, what is the noauto option for?[/QUOTE]
To not mount at bootup:

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

