---
title: "Is there a way to get a list of URLs from apt-get?"
date: 2009-03-26
forum: General Help
---

### Post by UbutnuFan on 2009-03-26
I don't have an internet connection on my pc but I can download all dependences (on other pc) that need for apt-get..

I need to install GCC (c++ compiler). So I need a list of URLs from apt-get to download packages depends on gcc..

Is there a way to do that?

---

### Post by evilaim on 2009-03-26
[http://ubuntuforums.org/showthread.php?t=79896](http://ubuntuforums.org/showthread.php?t=79896)

---

### Post by UbutnuFan on 2009-03-26
I think it's something like that :)
But how can I know what packages apt-get need to install other software?

For example, in Gentoo Linux we have something like that:
```
# emerge wget -pf | cut -f1 -d " "
http://distfiles.gentoo.org/distfiles/wget-1.11.4.tar.bz2

```
We can simply get a list of all urls (that depends on wget) by typing "emerge wget -pf". (In my case wget depends on 1 package (wget :) )

Is there a such command in ubuntu?

---

### Post by evilaim on 2009-03-26
do you mean: cat /etc/apt/sources.list
or: nano /etc/apt/sources.list 
that is the repo list, where all the packages are stored.

---

### Post by UbutnuFan on 2009-03-26
> **evilaim said:**
> do you mean: cat /etc/apt/sources.list
or: nano /etc/apt/sources.list 
that is the repo list, where all the packages are stored.
no-no-no-no-no! :)

An another example of using Gentoo Linux :)
```
# emerge kde -pf | cut -f1 -d " "

http://distfiles.gentoo.org/distfiles/openjpeg_v1_3.tar.gz
http://distfiles.gentoo.org/distfiles/poppler-data-0.2.1.tar.gz
http://distfiles.gentoo.org/distfiles/xmlrpc-c-1.16.06.tar.bz2
http://distfiles.gentoo.org/distfiles/findutils-4.5.4.tar.gz
http://distfiles.gentoo.org/distfiles/kdelibs-3.5.9.tar.bz2
http://distfiles.gentoo.org/distfiles/kde-3.5.9-seli-xinerama.tar.bz2
http://distfiles.gentoo.org/distfiles/kdelibs-3.5-patchset-14.tar.bz2
http://distfiles.gentoo.org/distfiles/poppler-0.10.5.tar.gz
http://distfiles.gentoo.org/distfiles/cmake-2.6.3.tar.gz
http://distfiles.gentoo.org/distfiles/kde-3.5.9-seli-xinerama.tar.bz2
http://distfiles.gentoo.org/distfiles/kdebase-3.5.9.tar.bz2
http://distfiles.gentoo.org/distfiles/kdebase-3.5-patchset-12.tar.bz2
http://distfiles.gentoo.org/distfiles/kdemultimedia-3.5.9.tar.bz2
http://distfiles.gentoo.org/distfiles/kdeedu-3.5.9.tar.bz2
http://distfiles.gentoo.org/distfiles/kdetoys-3.5.9.tar.bz2

```
So I can collect all those urls and I can download them from other computer (which has an internet connection). When that proccess will be done I'll just put all downloaded packages to the: /usr/portage/distfiles/
So I can install KDE (just for example) without an internet connection!
Great technology! :)

And what about Ubuntu? When I want to install some package but I don't have an internet connection and I don't know what packages Ubuntu need to install before it will be able to install my "desired some package" :) ...

---

### Post by coffeecat on 2009-03-26
**Edit**: What I posted isn't what you need. I'll get back.

---

### Post by UbutnuFan on 2009-03-26
Ok.. So I try to rehash my problem :)
Is there a way to know which packages depends on "some (one) package"?

---

### Post by Pig on 2009-03-26
I think that you want

```
sudo apt-get install package_name -qq --print-uris | cut -d\' -f2
```

on your internet-less computer.

Alternatively, you can also use Synaptic to mark the packages you want
but not install them and use "Generate package download script" from the "File" menu.

---

