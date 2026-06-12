---
title: "cant play encryptet DVDs even with css"
date: 2006-02-18
forum: Desktop Environments
---

### Post by supermihi on 2006-02-18
Hello,
I installed ubuntu dapper today and have one problem, I cant play most of my encrypted DVDs, even though I ran the script in /usr/share/doc/libdvdread*/examples, neither with xine nore with mplayer. It always says that libdvdcss can't open the dvd device. 
On my laptop, an IBM z60t, the cdrom device is /dev/scd0. Is that normal? I am used to /dev/hdc or something like that. Could that couse the problem? It may be a SATA drive since the hard disc is one.

---

### Post by cilynx on 2006-02-18
Did you run the dvdcss install with root permission or as your normal user?  You need to run it with root permissions:
```

sudo /usr/share/doc/libdvdread3/examples/install.sh

```

This is not what you want:
```

16:18:52 (63.16 KB/s) - `/tmp/libdvdcss.deb' saved [25178/25178]

dpkg: requested operation requires superuser privilege
rcw@pyth:/usr/share/doc/libdvdread3/examples$

```

This is:
```

16:20:21 (53.97 KB/s) - `/tmp/libdvdcss.deb' saved [25178/25178]

(Reading database ... 99518 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.5-1 (using /tmp/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.5-1) ...

rcw@pyth:/usr/share/doc/libdvdread3/examples$

```

Disclaimer:  Only follow this advice if you have the legal right to use libcssdvd.

---

### Post by nalmeth on 2006-02-18
Posting this here:
[http://ubuntuforums.org/forumdisplay.php?f=111](http://ubuntuforums.org/forumdisplay.php?f=111)
will get you better, more relevant results
good luck!

---

