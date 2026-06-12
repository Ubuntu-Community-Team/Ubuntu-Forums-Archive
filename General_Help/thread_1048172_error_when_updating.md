---
title: "error when updating"
date: 2009-01-23
forum: General Help
---

### Post by chriskin on 2009-01-23
when i search for new updates in the update manager i get a message saying this :
"E: The package cache file is corrupted
E: _cache->open() failed, please report.

W: Duplicate sources.list entry [http://ftp.ntua.gr](http://ftp.ntua.gr) intrepid-backports/main Packages (/var/lib/apt/lists/ftp.ntua.gr_pub_linux_ubuntu_dists_intrepid-backports_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://ftp.ntua.gr](http://ftp.ntua.gr) intrepid-backports/universe Packages (/var/lib/apt/lists/ftp.ntua.gr_pub_linux_ubuntu_dists_intrepid-backports_universe_binary-i386_Packages)"


can you tell me what this is supposed to mean and how am i to fix it?

:popcorn:

---

### Post by bgerlich on 2009-01-23
You have duplicated entries in /etc/apt/sources.lst, remove one of them.

---

### Post by chriskin on 2009-01-23
hehe
just that?


yes :) it worked :P how did they get there in the first place...? well, anyway
thanks :)
:KS

---

