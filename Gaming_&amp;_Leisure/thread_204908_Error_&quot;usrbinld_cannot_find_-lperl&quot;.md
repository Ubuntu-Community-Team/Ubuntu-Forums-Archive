---
title: "Error &quot;/usr/bin/ld: cannot find -lperl&quot;"
date: 2006-06-27
forum: Gaming &amp; Leisure
---

### Post by Christmas on 2006-06-27
I'm trying to install OpenMortal which is a Mortal Kombat clone. The problem is that after the "make" command it does something and then I get an error:
```
/usr/bin/ld: cannot find -lperl
collect2: ld returned 1 exit status
make[1]: *** [openmortal] Error 1
make[1]: Leaving directory `/home/christmas/openmortal-0.7/src'
make: *** [install-recursive] Error 1
```
The same goes with other programs. What is this lperl and how should I get rid of this error?

---

### Post by Footissimo on 2006-06-27
```
sudo apt-get install libperl-dev
```

Umm..also check you have libperl installed, if you haven't already :)

Hope that helps

edit: perl is a programming language

---

### Post by Christmas on 2006-06-27
Thanks a lot, that made it.
[quote=Footissimo]edit: perl is a programming language[/quote]
Yep I know that, I didn't know what should I install to make it work.

---

### Post by fonggiding on 2009-01-22
Installing the above sure helped my problem! thanks. For reference, I was installing ImageMagick.
Thanks!:KS

---

