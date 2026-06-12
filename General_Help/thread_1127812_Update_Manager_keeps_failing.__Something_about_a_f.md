---
title: "Update Manager keeps failing.  Something about a failed fetch."
date: 2009-04-16
forum: General Help
---

### Post by Mashuteichou on 2009-04-16
Here is what pops up when I hit check in the update manager, 

W: Failed to fetch [http://akirad.hfbk.net/dists/akirad-intrepid/Release.gpg](http://akirad.hfbk.net/dists/akirad-intrepid/Release.gpg)  Could not connect to akirad.hfbk.net:80 (193.174.241.68), connection timed out

W: Failed to fetch [http://akirad.hfbk.net/dists/akirad-intrepid/main/i18n/Translation-en_CA.bz2](http://akirad.hfbk.net/dists/akirad-intrepid/main/i18n/Translation-en_CA.bz2)  Unable to connect to akirad.hfbk.net http:

W: Some index files failed to download, they have been ignored, or old ones used instead

Then it just goes back to the main part.  There are 32 updates but I can't download any because this error pops up...

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory


So how do I fix this?  Some of the updates are important but it won't let me download any.  

Thanks for the help.

---

### Post by taurus on 2009-04-16
Maybe you want to try another server, System -> Administration -> Software Sources.

---

### Post by Vaedrah on 2009-04-16
Interestingly I have the same problem - I suspected a network problem but the forum rejected my question!

Even perfectly legitimate downloads e.g. synaptic have "fail to fetch errors"

The only solution I came across was specific syntax that was posted in another forum that I ran in a terminal that specifically downloaded necessary codecs - problem solved.

I suspect that if you have your own ISP connection then you may not have these hassles - if you connect through a proxy then even if this is configured properly, the connection may be unreliable. Perhaps Ubuntu has a "special setup" for this but I can't find one.

Perhaps, if anyone actually knows workarounds or syntax for missing files, or can explain why some may be unimportant, then this could be useful info.

---

### Post by Yashiro on 2009-04-16
It's failing because your Ubuntu mirror server is broken or you have some third party repositories enabled that are broken.

---

### Post by Qualitang on 2009-04-30
Hi there,

First post here so apologies for my newbness.

I'm having the same/similar problem - when i try to update it says that it "failed to fetch" "repository address" "403 Forbidden" "IP address". I've disabled all the third party thingy's in the software sources and i've changed the update server (a few times).  Still no joy. Any help here would be appreciated - and if there is a fix for this already posted i apologise, i have looked, and feel free to look down your nose in disgust!

PS; I recently had a problem with my wired connection - "device not managed" which has miraculously fixed itself - could this have caused the problem?..

Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by taurus on 2009-04-30
> **Qualitang said:**
> Hi there,

First post here so apologies for my newbness.

I'm having the same/similar problem - when i try to update it says that it "failed to fetch" "repository address" "403 Forbidden" "IP address". I've disabled all the third party thingy's in the software sources and i've changed the update server (a few times).  Still no joy. Any help here would be appreciated - and if there is a fix for this already posted i apologise, i have looked, and feel free to look down your nose in disgust!

PS; I recently had a problem with my wired connection - "device not managed" which has miraculously fixed itself - could this have caused the problem?..

Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz)  403 Forbidden [IP: 136.206.1.17 8080]
Some index files failed to download, they have been ignored, or old ones used instead.

Are you using proxy?

---

### Post by Qualitang on 2009-04-30
Now who feels like an idiot?!

yes proxy was set to my college proxy... I'm glad i apologized in advance! Sorry for wasting your time and many thanks for the uber quick reply!

---

