---
title: "Opps rm /usr/lib/libstdc++.so.6.0.5"
date: 2005-12-30
forum: General Help
---

### Post by lukeage on 2005-12-30
Yep thats right whilst trying to install oracle and linking some library files I deleted a file rather then a link. Normally i would have used apt-cache to find the file needed and then got back on with things - but i deleted libstdc++.so.6.0.5 which is required by apt-get.

I have the CD but i cannot find the deb package which contains libstdc++.so.6.0.5 and numerous google searchs have come up fruitless.

Does anyone know whereabouts on the cd i can find libstdc++.so.6.0.5. I am using breazy 5.10

Thanks in advance.

---

### Post by schilcha on 2005-12-30
I found it in package libstdc++6.
> 
$ dpkg-query -L libstdc++6
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/libstdc++6
/usr/share/doc/libstdc++6/copyright
/usr/share/doc/libstdc++6/README.Debian
/usr/share/doc/libstdc++6/changelog.Debian.gz
/usr/lib
/usr/lib/libstdc++.so.6.0.5
/usr/lib/libstdc++.so.6


Also, if you still can't find it on CD, try to copy it off a LiveCD

---

### Post by lukeage on 2005-12-30
[QUOTE=schilcha]I found it in package libstdc++6.


Also, if you still can't find it on CD, try to copy it off a LiveCD[/QUOTE]

Found it on the cd pool\main\g\gcc-4.0\

Thanks!

---

### Post by zucca on 2006-03-04
hiya,
I replaced the libstdc++.so.6.0.5 with an ancient version while messing around with links. I got amazed that just replacing the broken old library with the right file (from the cd), firefox works again.

zucca

---

