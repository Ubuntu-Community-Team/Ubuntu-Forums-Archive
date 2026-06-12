---
title: "Opera Install"
date: 2005-09-20
forum: Desktop Environments
---

### Post by karuptdata on 2005-09-20
I am trying to install the new opera without banners  :) however this is become more than i thought when i do dpkg -i it gives me this error dpkg -i opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb
Selecting previously deselected package opera.
(Reading database ... 71116 files and directories currently installed.)
Unpacking opera (from opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb) ...
dpkg: dependency problems prevent configuration of opera:
 opera depends on libqt3c102-mt; however:
  Package libqt3c102-mt is not installed.
dpkg: error processing opera (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 opera

so i tried to install libqt3c102-mt to no avail any help??

---

### Post by macgyver2 on 2005-09-20
I found [this package]("ftp://ftp.opera.com/pub/opera/linux/850/final/en/i386/shared/opera_8.50-20050916.6-shared-qt_en_etch_i386.deb") on another thread (courtesy of psychicdragon).  It works, no hassle.

---

### Post by karuptdata on 2005-09-20
So i found it as sone as i finished writing the post thanks my friend..

---

### Post by sbassett on 2005-09-20
You could try one the static qt debs...

[http://www.mirror.xac.net/pub/ftp.opera.com/linux/850/final/en/i386/static/opera-static_8.50-20050916.1-qt_en_i386.deb](http://www.mirror.xac.net/pub/ftp.opera.com/linux/850/final/en/i386/static/opera-static_8.50-20050916.1-qt_en_i386.deb)

---

