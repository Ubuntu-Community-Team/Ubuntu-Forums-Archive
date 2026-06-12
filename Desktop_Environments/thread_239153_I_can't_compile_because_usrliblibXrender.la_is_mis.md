---
title: "I can't compile because /usr/lib/libXrender.la is missing"
date: 2006-08-18
forum: Desktop Environments
---

### Post by walovaton on 2006-08-18
Hi, I am trying to compile some nautilus extensions:
nautilus-image-converter and nautilus-search-tool

Both of them complain that libXrender.la is missing with the following message:
grep: /usr/lib/libXrender.la: No such file or directory
/bin/sed: can't read /usr/lib/libXrender.la: No such file or directory
libtool: link: `/usr/lib/libXrender.la' is not a valid libtool archive
make[2]: *** [libnautilus-image-converter.la] Error 1
make[2]: se sale del directorio `/home/william/Desktop/nautilus-image-converter-0.0.5/src'
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio `/home/william/Desktop/nautilus-image-converter-0.0.5'
make: *** [all] Error 2


I have been googling around and I learn that this specific file was intentionally removed from the development package.  I don't mean to criticise that but there must be a way to compile this software without the .la file, is it?

Besides, if anyone can give me an ubuntu repository to get these packages it would be even better but the problem remains.  Just for curiosity I'd like to know how to fix this compilation problem.

Thanks to everyone in advance,

-William

---

### Post by dexter on 2006-08-20
just bumped into the same problem, try this

[http://ubuntuforums.org/showthread.php?t=238449](http://ubuntuforums.org/showthread.php?t=238449)

---

