---
title: "sudo apt-get update doesn't work."
date: 2006-04-09
forum: Desktop Environments
---

### Post by Sef on 2006-04-09
I am trying to fix the floppy bug in Breezy.  Followed the directions here:

[http://doc.gwos.org/index.php/Floppy_mount_issues]("http://doc.gwos.org/index.php/Floppy_mount_issues")

However, when I do sudo apt-get update, I get this message.  What can I do to fix this?

> sef@jokat1:~$ sudo apt-get update
E: The method driver /usr/lib/apt/methods/htp could not be found.


Here is what I added to sources.list:
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb htp://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse

---

### Post by frag79 on 2006-04-09
It's just a typo.

deb _htp_://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse

should be

deb_ http_://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse

---

### Post by Sef on 2006-04-09
Thank you.  Those little things are so important.  I look over it, but still missed it.  At least it is working now.

---

