---
title: "Installing Networked Multimedia (NMM)"
date: 2006-01-17
forum: General Help
---

### Post by Gijith on 2006-01-17
Hello All,

I desperately want to try and install [NMM]("http://www.networkmultimedia.org/NMM/index.html"). It's very intriguing to me and seems to offer many features, including video support for amaroK! The site offers a few options for install. I've tried compiling it 5 times now and have failed miserably each time. There's an insane number of external libraries and I can never get all of them in place. I've tried doing the simpler option and just apt-getting the deb, but I get the dreaded libqt3c102-mt error. I've seen a method for getting around this (for Skype) by converting a Fedora rpm. But I can't even find an rpm for Fedora. Does anyone have any experience trying to install NMM in Ubuntu? Does anyone have any suggestions?

Thanks

---

### Post by lamego on 2006-01-17
Maybe it would be better to post where you are stuck in compiling  from the source ?

---

### Post by Gijith on 2006-01-18
I start compiling, get pretty far, then this:

[B]collect2: ld returned 1 exit status
make[3]: *** [serverregistry] Error 1
make[3]: Leaving directory `/usr/local/src/nmm-0.9.1/apps/registry'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/local/src/nmm-0.9.1/apps'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/nmm-0.9.1'
make: *** [all-recursive-am] Error 2
dan@dan:/usr/local/src/nmm-0.9.1$ [/B]

I'm too new to really know what to make of it.

---

