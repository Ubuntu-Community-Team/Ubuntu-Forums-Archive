---
title: "Recuring Crashes libz.so.1.2.8"
date: 2013-11-07
forum: Desktop Environments
---

### Post by cnj on 2013-11-07
I am running 13.04 and have repeat crashes every 2 - 3 days. An error message, see attachment, quite often appears. Can I delete the file /libz.so.1.2.8 or will this wreck a package? Alternatively, can this file be replaced by another file?

CNJ

---

### Post by mc4man on 2013-11-07
zlib1g is part of a default install, without which you wouldn't have much of an install, so it's likely still installed, (.2.7.dfsg-13ubuntu2 in raring, libz.so.1.2.7
ck. with 
```
apt-cache policy zlib1g
```
However you've also caused libz.so.1.2.8 to be installed to /usr/local/lib, why did you do that?

---

### Post by cnj on 2013-11-07
Hi, I don't know how I managed to load the file at /usr/local/lib. However it was done, it was by accident. Does this mean I can remove it from this location?

---

### Post by mc4man on 2013-11-07
> **cnj said:**
> Hi, I don't know how I managed to load the file at /usr/local/lib. However it was done, it was by accident. Does this mean I can remove it from this location?
If you go about it properly, yes.

Did you ck. with apt-cache  that the raring zlib1g package is installed & **only** that package?
What's in /usr/local/lib concerning libz ?
```
ls /usr/local/lib |grep libz
```

As far as your posted error message - it's saying a program that uses libz in /usr/local/lib crashed, what program was that?

Just to see something - assuming default repo nautilus is used - what's this show?
```
ldd /usr/bin/nautilus |grep libz.so

```

*if you decide to just go ahead & remove that file(s) in /usr/local/lib then you better run this after removing but  before logging out or restarting
(assuming repo zlib1g is installed
```
sudo ldconfig
```

---

### Post by cnj on 2013-11-08
Hi MC4MAN thanks for the help.

The terminal outputs you asked about are:

colin@colin-MS-7309:~$ apt-cache policy zlib1g
zlib1g:
  Installed: 1:1.2.7.dfsg-13ubuntu2
  Candidate: 1:1.2.7.dfsg-13ubuntu2
  Version table:
 *** 1:1.2.7.dfsg-13ubuntu2 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) raring/main amd64 Packages
        100 /var/lib/dpkg/status
colin@colin-MS-7309:~$ ls /usr/local/lib |grep libz
libz.a
libz.so
libz.so.1
libz.so.1.2.8
colin@colin-MS-7309:~$ ldd /usr/bin/nautilus |grep libz.so
	libz.so.1 => /usr/local/lib/libz.so.1 (0x00007fea76ed9000)
colin@colin-MS-7309:~$ 

I am afraid these don't mean much to me? I am grateful for any help.

---

### Post by mc4man on 2013-11-08
Sure looks like you built & installed zlib.
(if you still have source folder you could cd to it in a terminal & run sudo make uninstall or just do manually as in - 

Open a terminal & run this command
```
sudo rm -f /usr/local/lib/libz.*
```
Then maybe not needed but run anyway
```
sudo ldconfig
```

Now ck. that nautilus is using the proper libz - 
```
ldd /usr/bin/nautilus |grep libz.so
```

(should > to /lib/[COLOR="#0000CD"]x86_64-linux-gnu[/COLOR]/libz.so.1 or the blue would be 'i386-linux-gnu' if on a 32 bit install

If all is well there are likely a few other files in /usr/local/ that can be removed, ck. & remove
(look for
 /usr/local/lib/pkgconfig/zlib.pc 
/usr/local/share/man/man3/zlib.3 #may be 3 or may be different number
/usr/local/include/zconf.h
/usr/local/include/zlib.h

---

### Post by cnj on 2013-11-10
Hi I have carried out your recommendations and will see what happens over the next few days.

Thanks for your help.

---

