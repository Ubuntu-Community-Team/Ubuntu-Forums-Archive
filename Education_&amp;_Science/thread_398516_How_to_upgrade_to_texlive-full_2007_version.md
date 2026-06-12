---
title: "How to upgrade to texlive-full 2007 version"
date: 2007-04-01
forum: Education &amp; Science
---

### Post by LJM on 2007-04-01
I've been wondering how to upgrade to texlive-full 2007 version, which was released last February. 

What commands should I run? Should I just install the new version "on top of" the older one? 

Thanks in advance!

---

### Post by kleeman on 2007-04-01
The 2007 packages have just entered Debian experimental. If you want them you can get them here:

[http://ftp.debian.org/debian/pool/main/t/texlive-base/](http://ftp.debian.org/debian/pool/main/t/texlive-base/)

Grab all the debs with 2007 in them and try installing all together with
sudo dpkg -i *.deb *.deb (where *.deb is the package name)

I haven't tried this so it may not work since these packages have a complex set of dependencies. If they don't you may need to download the dsc orig.tar.gz and diff files and compile yourself. I would not use experimental Debian in my apt source.list file as it may pull in bucketloads of unstable software....

---

