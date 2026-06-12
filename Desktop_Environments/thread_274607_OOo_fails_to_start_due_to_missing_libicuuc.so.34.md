---
title: "OOo fails to start due to missing libicuuc.so.34"
date: 2006-10-10
forum: Desktop Environments
---

### Post by zorankovacevic on 2006-10-10
Hi all,

I have installed Dapper. When I try to run OOo, it says:

```
zoran@eraser:~$ openoffice
/usr/lib/openoffice/program/soffice.bin: error while loading shared libraries: libicuuc.so.34: cannot open shared object file: No such file or directory

```

I can't seem to find any related postings, except for this one:
[http://lists.debian.org/debian-openoffice/2006/07/msg00142.html](http://lists.debian.org/debian-openoffice/2006/07/msg00142.html)

There is a file called libicuuc.so.34.1 on my system:
```

zoran@eraser:~$ locate libicuuc.so.34
/usr/lib/libicuuc.so.34.1

```

I thought I'd symlink it to libicuuc.so.34, but that gives a segfault:

```

zoran@eraser:~$ openoffice
/usr/lib/openoffice/program/soffice: line 233:  7328 Segmentation fault      "$sd_prog/$sd_binary" "$@"

```

I have already done a remove --purge of all OOo packages and reinstalled everything.

Any clues on how to bypass the library issue and get OOo working? The rest of Dapper is working fine btw.

Best regards,
Zoran

---

### Post by pacodani on 2006-10-11
Same error here. Is there any solution?

---

