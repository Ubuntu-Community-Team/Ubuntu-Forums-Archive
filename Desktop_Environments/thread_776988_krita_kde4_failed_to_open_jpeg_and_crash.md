---
title: "krita kde4 failed to open jpeg and crash"
date: 2008-05-01
forum: Desktop Environments
---

### Post by OnlyWhisky on 2008-05-01
Hello, I have krita kde4 package installed as part of hardy heron and I wish to open jpeg, but it crash.

user@server:/usr/bin$ krita
krita(9865) KFileItem::isDir:  KFileItem::isDir can't say -> false
krita(9865) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"
krita(9865) KMimeTypeFactory::parseMagic: Now parsing  "/home/user/.local/share/mime/magic"
ASSERT: "exifIO" in file /build/buildd/koffice2-1.9.96.0~that.is.really.1.9.95.3/filters/krita/jpeg/kis_jpeg_converter.cc, line 285
first:  true
child:  "Layer 1"
first:  true
child:  "Layer 1"
first:  true
child:  "Layer 1"
first:  true
child:  "Layer 1"
KCrash: crashing... crashRecursionCounter = 2
KCrash: Application Name = krita path = <unknown> pid = 9865
sock_file=/home/user/.kde4/socket-server/kdeinit4__0
---------------------------------------------------------------
I know koffice4 is still under development, but there are packages in repository so why not to fix them? ;) Really lack of krita4, because krita3 is slow and gimp is so-so. Thank you!

---

