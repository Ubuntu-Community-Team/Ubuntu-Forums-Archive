---
title: "libpcre.so.0 MudMagic error on prog start"
date: 2006-09-11
forum: Desktop Environments
---

### Post by Omnios on 2006-09-11
Hi I just installed the latest Mud Magic mud client 1.9 by using alien to convers a rpm package and it installed ok. Now the problem I am having is that when I try to start it I get the following error.
```

/usr/bin/mudmagic-bin: error while loading shared libraries: libpcre.so.0: cannot open shared object file: No such file or directory

```
 
 Also this seemed to be a issue before as for an older version someone did a system link to point the missing lib to the current one. Anywone have any suggestions.

---

### Post by nikhilk on 2006-09-11
Can you find out if the libpcre.so.0 file is present on your system and if yes, where?

---

### Post by Omnios on 2006-09-11
DId a file search and nothing there.

---

### Post by nikhilk on 2006-09-11
> **Omnios said:**
> Also this seemed to be a issue before as for an older version someone did a system link to point the missing lib to the current one.

Could you kindly elaborate?

---

### Post by Omnios on 2006-09-11
K solved the libpcre.so.0 prob,em by making a link=
```

sudo ln -s /usr/lib/libpcre.so.3 /usr/lib/libpcre.so.0

```  This solved that problem now im getting this error.
```

tom@miko:~$ mudmagic
/usr/bin/mudmagic-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /usr/bin/mudmagic-bin)
/usr/bin/mudmagic-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libmudmagic.so.0)
/usr/bin/mudmagic-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/mudmagic/libs/libcurl.so.0)

``` 
 Anyways im just got this error and am looking into it.

so far seems I have this file
```

tom@miko:~$ locate libc.so.6
/lib/tls/libc.so.6
/lib/tls/i686/cmov/libc.so.6
/lib/libc.so.6
tom@miko:~$

```

---

### Post by Omnios on 2006-09-11
Hi hi got it to work by getting the edgy libc6 packege from.
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
[B]
[/B]

---

