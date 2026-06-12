---
title: "getting ext4 in 8.10"
date: 2009-04-26
forum: General Help
---

### Post by shortridge11 on 2009-04-26
I'm putting a home file server together and i wanted to use ext4, but i don't want to use 9.04 yet, because i don't think it's stable enough.  Has 8.10 been recompiled to allow for ext4? or is that going to take a bit of legwork on my part...

---

### Post by Tim Sharitt on 2009-04-26
If you want to use ext4 in 8.10, you will need to compile a custom kernel with ext4 support (2.6.28 or later). You can get the latest kernel source code from [http://www.kernel.org](http://www.kernel.org).

You will also need the latest version of e2fsprogs, available from [ftp://ftp.kernel.org/pub/linux/kernel/people/tytso/e2fsprogs/](ftp://ftp.kernel.org/pub/linux/kernel/people/tytso/e2fsprogs/).

You can find more information at [http://ext4.wiki.kernel.org/index.php/Ext4_Howto](http://ext4.wiki.kernel.org/index.php/Ext4_Howto).

---

