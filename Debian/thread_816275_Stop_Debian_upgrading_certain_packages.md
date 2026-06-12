---
title: "Stop Debian upgrading certain packages?"
date: 2008-06-02
forum: Debian
---

### Post by miggols99 on 2008-06-02
I've installed the libxft2 and libfreetype6 packages from the Ubuntu repos, and they made my fonts nice to look at :) But apt wants to upgrade them to the Debian releases, which aren't patched for subpixel hinting. Is there any way I can tell apt to leave these two packages alone?

---

### Post by inclusivedisjunction on 2008-06-03
You can tell apt to "hold" them.

```
echo "package_name hold"|dpkg --set-selections 
```

to hold a package, and

```
echo "package_name install"|dpkg --set-selections
```

I got this from the Debian forums, BTW.

[http://forums.debian.net/viewtopic.php?t=240](http://forums.debian.net/viewtopic.php?t=240)

---

### Post by kellemes on 2008-06-03
Use pinning..
As an example.. I don't want't my fglrx-driver packages to be upgraded, so I "pin" them by including the following lines in /etc/apt/preferences

```
Package: fglrx-kernel-src
Pin: version 8.43.2-2
Pin-Priority: 1001

Package: fglrx-driver
Pin: version 8.43.2-2
Pin-Priority: 1001

```

More info on pinning. [http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin]("http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin")

---

