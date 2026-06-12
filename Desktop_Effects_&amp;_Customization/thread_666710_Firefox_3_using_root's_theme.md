---
title: "Firefox 3 using root's theme"
date: 2008-01-13
forum: Desktop Effects &amp; Customization
---

### Post by Gigamo on 2008-01-13
Hey.

So I decided to try out Firefox 3 Beta 2 to see what all the fuss is about, it using GTK themes now. My problem is that it uses that flat, dull, boring and gray theme you get when you launch an app with su or sudo. What could cause this/How should I make it use my desktop's theme? :D

Help appreciated!

---

### Post by chrisccoulson on 2008-01-13
You're not by any chance using 32-bit Firefox on a 64-bit system are you? If you are, you need the 32-bit GTK engine for your current theme, which may not be installed.

---

### Post by Gigamo on 2008-01-13
> **chrisccoulson said:**
> You're not by any chance using 32-bit Firefox on a 64-bit system are you? If you are, you need the 32-bit GTK engine for your current theme, which may not be installed.

Aaah, i expect this to be the case. How should I go with installing the 32 bit gtk engine? It probably will error.

---

### Post by chrisccoulson on 2008-01-13
First of all, you need to make sure that you have ia32-libs installed.
```
sudo apt-get install ia32-libs
```

This package contains 32-bit versions of the most common GTK engines. If your current theme is using a different engine, you will need to download the i386 deb (gtk2-engines-<*engine_name*>), and extract the package:
```
dpkg -x gtk2-engines-<*engine_name*>_<*version*>_i386.deb .
```
then copy the .so files from the package in to /usr/lib32/gtk-2.0/2.10.0/engines
```
sudo cp ./usr/lib/gtk-2.0/2.10.0/engines/*.so /usr/lib32/gtk-2.0/2.10.0/engines/
```

---

### Post by Gigamo on 2008-01-14
Sorry but that didn't fix it :(. I have now seen that the problem is there in Firefox 2 as well (although not as badly), and with 64bit firefox as well. Also, the murrine engine is a tar.bz package that I had to compile myself, so there is no specific i386 installer for it.

Anyone? :D

---

