---
title: "Corrupted /usr/lib/ files"
date: 2009-02-08
forum: Desktop Environments
---

### Post by legolas558 on 2009-02-08
Hello there,

I have corrupted (by mistake) some files in /usr/lib/.

This is my ldconfig output:

```
legolas558@localhost:~$ sudo ldconfig
/sbin/ldconfig.real: /usr/lib/libsmjpeg-0.2.so.0 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/ld-linux.so.2 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libstdc++-libc6.2-2.so.3 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libdb.so.2 is not a symbolic link
```

I have reinstalled the relative packages without success. Also, this is my output when running 'wine':

```
wine: /usr/bin/../lib/libc.so.6: version `GLIBC_2.3.4' not found (required by wine)
wine: /usr/bin/../lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/bin/../lib/libwine.so.1)
wine: /usr/bin/../lib/libc.so.6: version `GLIBC_2.3' not found (required by /usr/bin/../lib/libwine.so.1)
wine: /usr/bin/../lib/libc.so.6: version `GLIBC_2.3.4' not found (required by /usr/bin/../lib/libwine.so.1)
wine: /lib/ld-linux.so.2: version `GLIBC_2.1.1' not found (required by /usr/bin/../lib/libc.so.6)
wine: /lib/ld-linux.so.2: version `GLIBC_2.2.3' not found (required by /usr/bin/../lib/libc.so.6)
wine: /lib/ld-linux.so.2: version `GLIBC_2.2' not found (required by /usr/bin/../lib/libc.so.6)
wine: /usr/bin/../lib/libc.so.6: version `GLIBC_PRIVATE' not found (required by /lib/tls/i686/cmov/libdl.so.2)

```

Can somebody please tell me how to fix these issues? Thanks

---

### Post by Vadi on 2009-02-08
Tried reinstalling linux-headers-2.6.27-11 ?

---

### Post by legolas558 on 2009-02-15
> **Vadi said:**
> Tried reinstalling linux-headers-2.6.27-11 ?

Yes, absolutely nothing changed. There's to say that I was using a wine package provided by winehq. But this does not explain the ldconfig errors, that are probably due to some of my direct messing with /usr/lib/ files (I didn't do it on purpose but accidentally)

Please don't tell me that I have to reinstall Ubuntu...

---

### Post by Vadi on 2009-02-15
I've never encountered this, so I'm not sure. Hope someone who's an expert picks this up.

---

### Post by squinter on 2009-05-15
I got same problem :(

I tried reinstalling linux headers and all the libstdc++ packages with no luck.

Please someone help!?

---

### Post by squinter on 2009-05-15
BTW, I'm running Ubuntu 32bit 9.04

and this is what I got when running sudo ldconfig:

/sbin/ldconfig.real: /usr/lib/libstdc++-libc6.2-2.so.3 is not a symbolic link

Seems like it was a symbolic link but now it isn't and ldconfig.real does not like this?? May be there's a way to make it like the non symbolic link now??

---

