---
title: "f-spot 0.1.5"
date: 2005-12-26
forum: Deferred/Invalid Requests
---

### Post by F for Fragging on 2005-12-26
Could f-spot 0.1.5 please be backported? It's already in Dapper - [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=f-spot&searchon=names&subword=1&version=dapper&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=f-spot&searchon=names&subword=1&version=dapper&release=all) - Currently we have 0.1.3 in Breezy. 0.1.4 and 0.1.5 fixed some bugs, and a few features which are quite useful for me. For example, newest photos are displayed first and you can now browse through photos with the arrow keys while in edit mode. Changes might not seem to be much, but I'd appreciate it if it could be backported. As far as I know when I compiled it myself, it doesn't introduce any new dependencies, so it is backportable?

---

### Post by nehalem on 2006-01-02
I couldn't agree more.  The new version introduces much better tagging, some better deletion stuff, and exporting to gallery 2.  

Any chance or does it require a newer version of mono???

---

### Post by jdong on 2006-01-02
Currently awaiting mono work.

---

### Post by Hezekiah on 2006-01-04
I recompiled f-spot from Sid (same version + revision that's in Dapper from what I can tell?) using the existing Breezy Mono setup.

If anyone is interested, and I won't be stepping on too many toes by doing so, I can make the deb available for download until an official backport is made.

NOTE:  I haven't tested this home made backport at all really.  I just added the Sid deb-src, did an apt-get build-deps; apt-get source; dpkg-buildpackage; on it.

---

### Post by ceagan on 2006-02-12
The export to flickr option no longer works and I would really like to use this feature. It appears to be fixed upstream in the newer releases. Has anyone been able to build / install the latest version on Breezy?

Please send me a .deb package if you have one!

---

### Post by Hezekiah on 2006-02-13
I have the deb uploaded here:
[http://0ok.org/wiki/wiki.pl?action=view&id=fspot]("http://0ok.org/wiki/wiki.pl?action=view&id=fspot")

As I said before, this is NOT even remotely well tested.  I have not tested any of the export functions, and I only have a few photos in it currently.  But the few things I have tested work, and it does seem to be smoother than the version in Breezy.

PLEASE do not submit any bugs about this package to the Ubuntu and/or Backports folks.  They have nothing to do with it.

---

