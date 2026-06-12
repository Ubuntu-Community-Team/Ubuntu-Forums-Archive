---
title: "msttcorefonts offline install"
date: 2009-02-15
forum: General Help
---

### Post by don-robbery on 2009-02-15
Recently I had trouble installing msttcorefonts as the machine had no internet access.  I found an rpm package only and converted it to a *.deb file using alien.

It can be found here and includes all the fonts .ttf files.

[http://rapidshare.com/files/198591905/msttcorefonts_2.0-1_i386.deb.html](http://rapidshare.com/files/198591905/msttcorefonts_2.0-1_i386.deb.html)
and here
[http://www.MegaShare.com/dl/79/NzgYbMiFKP/msttcorefonts_2.0-1_i386.deb](http://www.MegaShare.com/dl/79/NzgYbMiFKP/msttcorefonts_2.0-1_i386.deb)

1. Download
2. sudo dpkg -i msttcorefonts_2.0-1_i386.deb
3. fc-cache -rv (possibly sudo fc-cache -rv)

Hope this helps and works for others.

For those that are interested I found the rpm here;
[http://rpm.pbone.net/index.php3?stat=26&dist=0&size=3502929&name=msttcorefonts-2.0-1.i386.rpm](http://rpm.pbone.net/index.php3?stat=26&dist=0&size=3502929&name=msttcorefonts-2.0-1.i386.rpm)

Laters

---

