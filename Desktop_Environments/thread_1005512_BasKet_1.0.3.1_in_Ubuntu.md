---
title: "BasKet 1.0.3.1 in Ubuntu?"
date: 2008-12-08
forum: Desktop Environments
---

### Post by ba0bab on 2008-12-08
Hi,

I love notetaking app BasKet as I think alot of ppl do - I'd really like the newest version, the one those lucky bastards using KDE are using.

I tried doing this:
```

sudo apt-get build-dep basket
E: Build-dependencies for basket could not be satisfied.

```

I then tried this:
```

sudo apt-cache showsrc basket
Package: basket
Binary: basket, basket-kontact-integration
Version: 1.0.2-5
Priority: optional
Section: universe/kde
Maintainer: Debian KDE Extras Team <pkg-kde-extras@lists.alioth.debian.org>
Build-Depends: debhelper (>= 5), autotools-dev, kdelibs4-dev (>= 4:3.5.6), kdepim-dev (>= 4:3.5.9-2), libgpgme11-dev, quilt (>= 0.40), autoconf, libtool, automake
Architecture: any
Standards-Version: 3.7.2
Format: 1.0
Directory: pool/universe/b/basket
Files:
 21c53e2436182eaa29c54f2be0c0693f 1206 basket_1.0.2-5.dsc
 d71c62a56de9cc32ba2633e63e99071f 6046068 basket_1.0.2.orig.tar.gz
 1bb2cfc33db749848f6633e093f58e92 37773 basket_1.0.2-5.diff.gz
Uploaders: Sune Vuorela <debian@pusling.com>
Homepage: http://basket.kde.org/
Checksums-Sha1: 
 8f227c45d84e3739750d39b32700b3329b8c3c84 6046068 basket_1.0.2.orig.tar.gz
 06a57bcf131532b151d65756b2d1f692a849e730 37773 basket_1.0.2-5.diff.gz
Checksums-Sha256: 
 8c5715f700724b274d162074b601947136d8b71caa36bc3fa36a7b95836b997e 6046068 basket_1.0.2.orig.tar.gz
 d882f93db3b56dc38d3edfeda440497598408ed7842034cef018f6cb02f4065a 37773 basket_1.0.2-5.diff.gz

```

...and that is as far as my skillz will take me. Is it even possible to do? tried googling and searched the forums as well as a couple of Ubuntu-blogs, no dice. The closest is this blog, which tells how to do it on Debian Lenny:

[http://vivapinkfloyd.blogspot.com/2008/07/how-to-compile-and-install-basket-from.html](http://vivapinkfloyd.blogspot.com/2008/07/how-to-compile-and-install-basket-from.html)

Since Debian and Ubuntu are so similar I guess it is possible? Or?

Thanks in advance,
Emile

---

### Post by carml on 2008-12-08
Have you got in Debian something similar to Synaptic?I mean an utility you can find by the System menù(or similar),if you are using a GUI.
If it's so,you can find there a previous version of Basket.
Tell me if I helped you or if you need more help:p.

---

### Post by carml on 2008-12-08
Have you got in Debian something similar to Synaptic?I mean an utility you can find by the System menù(or similar),if you are using a GUI.
If it's so,you can find there a previous version of Basket.
Tell me if I helped you or if you need more help:p.

---

### Post by ba0bab on 2008-12-09
I think you misunderstood me - I don't want a previous version, but the newest version - the one in the Ubuntu repo's is 1.0.2.5, the newest version for KDE is 1.0.3.5. 

It is possible to install the newest version from source in Debian under GNOME, so it must be possible in Ubuntu as well, right?

---

### Post by kabala on 2009-01-02
Yes, it is possible. I made it :) 

I encouraged only 2 problems during the configure step:
1) Qt 3.0 headers were missing 
2) kde headers were missing 

I'm not sure, but the command
sudo apt-get install kdelibs4-dev libqt3-headers

shoud do the job.

Then as normal you can begin the installation from source:
./configure
make 
make install #as root

---

### Post by ba0bab on 2009-01-04
Thank you that worked like a charm! cool burger :)

---

### Post by pdub on 2009-02-13
Thanks kabala and ba0bab, this post was helpful.

---

### Post by ba0bab on 2009-02-14
You're welcome. One thing though: Version 1.0.3.1 doesn't support encryption of baskets, which is quite important for me and perhaps others as well. So before you bother upgrading manually, be prepared to give up encryption. Or maybe a newer version has been released when you read this.

/E

---

