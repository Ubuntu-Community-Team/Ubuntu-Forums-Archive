---
title: "Simple Backup"
date: 2005-11-28
forum: Closed Requests
---

### Post by Limulus on 2005-11-28
For backports or extras, as applicable: Simple Backup

[http://www.linux.com/article.pl?sid=05/11/22/2110251](http://www.linux.com/article.pl?sid=05/11/22/2110251)
[http://sourceforge.net/projects/sbackup/](http://sourceforge.net/projects/sbackup/)

Its already in a DEB and was designed for Ubuntu :)

---

### Post by strikeforce on 2005-11-29
Its already in breezy make sure you have the necessary repo's

---

### Post by Limulus on 2005-11-29
strikeforce: You're right!  Sorry about that; let me modify my request then:

Can version 0.9-1 be added to backports? (0.8-1 is in Breezy's repositories)

---

### Post by strikeforce on 2005-11-29
Unforutnately the version in dapper is 0.7 still

> 
(mychroot)marc@ubuntu:~$ apt-cache show simplebackup
Package: simplebackup
Priority: optional
Section: universe/utils
Installed-Size: 84
Maintainer: Christian Garbs <debian@cgarbs.de>
Architecture: all
Version: 0.0.7-1
Depends: bzip2, coreutils | stat
Filename: pool/universe/s/simplebackup/simplebackup_0.0.7-1_all.deb
Size: 7608
MD5sum: 152ffb26430f4a748231f0b0a3168c2f
Description: Simple backup tool
 The included script performs a nice and easy file based backup.  It
 can easily be extended to include database dumps or save the output
 from `fdisk -L` and other things as well.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu


---

### Post by Limulus on 2005-12-03
strikeforce: Ah!  There's been some confusion; that's "simplebackup".  The package I was talking about is "sbackup".  Breezy has 0.8-1 while Dapper has 0.9-1: [http://packages.ubuntu.com/dapper/admin/sbackup](http://packages.ubuntu.com/dapper/admin/sbackup)

Could it be backported now that that's been cleared up? :)

---

### Post by jdong on 2005-12-03
Looks good, I'll investigate further.

---

### Post by fergus on 2005-12-08
Any update on this backport?

---

### Post by Limulus on 2005-12-09
fergus: If you just want to run the latest version, download the DEB from [http://sourceforge.net/projects/sbackup/](http://sourceforge.net/projects/sbackup/) and install it with *sudo dpkg -i [filename]* using Terminal.  That's what I did and it works great :)  I thought others would like it too, which is why I requested it to be backported.

---

### Post by jdong on 2005-12-09
works well, sent for build.

---

