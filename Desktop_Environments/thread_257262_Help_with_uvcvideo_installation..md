---
title: "Help with uvcvideo installation."
date: 2006-09-14
forum: Desktop Environments
---

### Post by LPomfrey on 2006-09-14
I'm trying to install uvc using the following commands:

> svn checkout [http://svn.berlios.de/svnroot/repos/linux-uvc/](http://svn.berlios.de/svnroot/repos/linux-uvc/)
cd linux-uvc/linux-uvc/trunk
make
sudo make install

However after make and sudo make install I'm getting the following error:

> Building USB Video Class driver...
/bin/sh: line 0: cd: /lib/modules/2.6.15-26-386/build: No such file or directorymake: *** [uvcvideo] Error 1


Are there any packages I need to get to be able to build this? :confused: 


It's probably really simple, but I only installed Linux yesterday so I'm not exactly up to speed on everything.

---

### Post by lamego on 2006-09-14
You will need the linux kernel headers:
```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by LPomfrey on 2006-09-14
> **lamego said:**
> You will need the linux kernel headers:
```
sudo apt-get install linux-headers-$(uname -r)
```

That did it. Thanks a lot. O:)

---

