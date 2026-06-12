---
title: "Permissions problem on mounted ISO image"
date: 2009-05-09
forum: General Help
---

### Post by JabaDisa on 2009-05-09
I've mounted a ISO image using:
```
sudo mount img.iso /media/ISO/ -t iso9660 -o loop
```

But when I do "ls /media/ISO/" I get:
```

-rwx------ 1  503  503   61440 2005-07-15 00:23 autorun.exe
-rwx------ 1  503  503      31 2002-05-17 21:40 autorun.inf
dr-xr-xr-x 1 root root    2048 2005-09-01 07:03 config
dr-xr-xr-x 1 root root    2048 2005-08-14 02:19 documentation
-rwx------ 1  503  503   15073 2005-08-26 23:12 readme.htm

```

How do I fix this so my user has r-x access? And who is that 503 user?

Additional info:
- The ISO image is located on a physical DVD mounted in /media/cdrom0
- The permissions for /media/ISO (when not mounted) are 0777.
- mount is using loop device /dev/loop0

Thanks in advance.

---

### Post by JabaDisa on 2009-05-09
Problem solved when I disabled the Rock Ridge extensions.

```
sudo mount img.iso /media/ISO -o norock,loop
```

The mount man page says:
> 
...when Rock Ridge is in use, the  filesystem  is indistinguishable from a normal UNIX file system, And respectively, subject to permission issues :) Other ISOs mount perfectly, but this one works with norock only :)

---

