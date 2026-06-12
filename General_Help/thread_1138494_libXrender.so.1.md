---
title: "libXrender.so.1"
date: 2009-04-26
forum: General Help
---

### Post by EEPS on 2009-04-26
Hi guys, I just upgraded to 9.04 through the update manager. Since then, a program I use called eagle has stopped working. The error I get is: "/opt/eagle-5.4.0/bin/eagle: error while loading shared libraries: libXrender.so.1: cannot open shared object file: No such file or directory"

I have libXrender1 installed. I can even find the specific file it is looking for, its in /usr/lib/libXrender.so.1. When I look at the file, it appears to be a sym link to libXrender.so.1.3.0 in the same directory. Does any one know why this is not working? I am running 64bit 9.04 btw.

Thanks

---

### Post by spiderbatdad on 2009-04-26
not sure but it seems eagle might be looking for the lib in /opt/

maybe this will list dependencies and shared librries for you
```
ldd /opt/eagle-5.4.0/bin/eagle

```

---

### Post by EEPS on 2009-04-26
This is what I get:

```

ldd /opt/eagle-5.4.0/bin/eagle
	linux-gate.so.1 =>  (0xf7f41000)
	libXrender.so.1 => not found
	libXrandr.so.2 => not found
	libXcursor.so.1 => not found
	libXft.so.2 => not found
	libfreetype.so.6 => not found
	libfontconfig.so.1 => not found
	libXext.so.6 => not found
	libX11.so.6 => not found
	libdl.so.2 => /lib32/libdl.so.2 (0xf7f27000)
	libXi.so.6 => not found
	libpng12.so.0 => not found
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf7f0e000)
	librt.so.1 => /lib32/librt.so.1 (0xf7f04000)
	libjpeg.so.62 => not found
	libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf7e15000)
	libm.so.6 => /lib32/libm.so.6 (0xf7def000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7de0000)
	libc.so.6 => /lib32/libc.so.6 (0xf7c7c000)
	/lib/ld-linux.so.2 (0xf7f42000)
	libz.so.1 => not found


```

---

### Post by EEPS on 2009-04-26
Ok, I got it to install. I did a clean install instead of an upgrade of ubuntu for other reasons. It still would not install though. I then installed eagle from apt, but it is a painfully old version. After I uninstalled this version though, the new version was able to run and install.

---

### Post by spiderbatdad on 2009-04-26
great. when you compile your own version, usually in the documentation it will tell you how to set flags to compile to a specific directory...like /etc or /usr instead of /opt. Other other hand you can compile to opt, but then it is neccesary to copy all the dependencies over...sometimes tricky.

---

