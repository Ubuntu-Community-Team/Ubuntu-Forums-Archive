---
title: "Self unrooting."
date: 2006-08-06
forum: Desktop Environments
---

### Post by Brbotalnik on 2006-08-06
I've somehow managed to remove my username from all supplemental groups (was experimenting with usermod)...that means I cannot sudo anymore and therefore can't do anything what needs root privilege. Is there a way to regain root access?

thx for any help.

---

### Post by Sutekh on 2006-08-07
Sure.  First you need to boot your system with root access, so that you can return your user to the appropriate groups.

If it's available, you can boot into Recovery Mode from the GRUB menu.  After Ubuntu loads, you should be left at a root prompt, similar to
```
root@ubuntu:~#
```
Then you can place your user in the required groups (admin being the one to use sudo).  I would use the adduser command.
```
adduser <username> <groupname>
```

---

### Post by scxtt on 2006-08-07
when you boot into recovery mode, you should just need to add your username to the following groups (replace scxtt w/ your username):
```
:> cat /etc/group | grep scxtt
adm:x:4:scxtt
dialout:x:20:cupsys,scxtt
cdrom:x:24:haldaemon,scxtt
floppy:x:25:haldaemon,scxtt
audio:x:29:scxtt
dip:x:30:scxtt
video:x:44:scxtt
plugdev:x:46:haldaemon,scxtt
lpadmin:x:106:scxtt
scanner:x:110:cupsys,scxtt
scxtt:x:1000:
admin:x:111:scxtt
```

---

### Post by Brbotalnik on 2006-08-07
Oh great, all works like a charm again. Tnx.

---

