---
title: "AviDemux 2.1.2"
date: 2006-06-15
forum: Desktop Environments
---

### Post by jISh on 2006-06-15
Can anybody get this to work on Ubuntu?
I enabled the unstable repository, and went to get this new version (I NEED it, as it fixes a bug that prevents me from doing some things in 2.1.1), but I get this

```

avidemux:
  Depends: libc6 (>=2.3.6-6) but 2.3.6-0ubuntu20 is to be installed
 Depends: libdirectfb-0.9-24  but it is not installable
  Depends: libfaac0 (>=1.24+cvs20060416) but 1.24-0.3 is to be installed
  Depends: libfaad2-0 (>=2.0.0+cvs20060416) but 2.0.0-0.5 is to be installed
  Depends: libgcc1 (>=1:4.1.0) but 1:4.0.3-1ubuntu5 is to be installed
 Depends: libmozjs0d  but it is not installable
  Depends: libstdc++6 (>=4.1.0) but 4.0.3-1ubuntu5 is to be installed

```

Anybody have this version working? How? Thanks.

---

### Post by jISh on 2006-06-15
Sorry to bump, but I REALLY need this program, does anybody know?

---

### Post by tedt on 2006-06-16
Unstable is not an ubuntu repository designation - what repository are you using?

---

### Post by reclusivemonkey on 2006-06-17
[QUOTE=jISh]Sorry to bump, but I REALLY need this program, does anybody know?[/QUOTE]


Works fine for me; I just have the regular Ubuntu repositories.

[http://www.reclusivemonkey.com/images/Screenshot-23.png](http://www.reclusivemonkey.com/images/Screenshot-23.png)

---

### Post by SadaraX on 2006-06-26
jISh:
You have some dependancies that are out of date for that version of Avidemux. You can upgrade your system to get it to work. However, this may also help, I literally just made it a minute ago
[http://www.ubuntuforums.org/showthread.php?t=203898](http://www.ubuntuforums.org/showthread.php?t=203898)


tedt:
Version 2.1.2 is in the multiverse, and maintained by Christian Marillat, location:
pool/multiverse/a/avidemux/avidemux_2.1.2-0.0ubuntu2_i386.deb

Not that it much matters, but I will be making an apt-repository specifically for Avidemux when it goes to version 2.2.0 in a few weeks here. I work on the code passively and help out a lot with the site docs. :) Heck, does anyone know how you can apply to become a package maintainer for ubuntu?

---

