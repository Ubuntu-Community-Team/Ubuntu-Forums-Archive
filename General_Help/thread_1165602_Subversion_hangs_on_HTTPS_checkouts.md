---
title: "Subversion hangs on HTTPS checkouts"
date: 2009-05-20
forum: General Help
---

### Post by N3X15 on 2009-05-20
I've noticed that, on my Ubuntu desktop unit, when I try to checkout an HTTPS-hosted repository, SVN hangs and I have to forcefully kill it (killall -9 svn).  I suspect this has to do with either a borked SSL package or a broken dependancy, yet apt-get check reports that there are no broken dependancies, and reinstalling openssl and subversion did not help.  

Ubuntu Jaunty Jackalope (9.04) x86
Pentium Core Duo 3.0Ghz
4.0GB RAM

Additional info:  performing the same checkout on my Debian server finished without a hang.

---

### Post by danep on 2010-01-25
A bit late, obviously, but could this be related?
[http://ubuntuforums.org/showthread.php?t=948900](http://ubuntuforums.org/showthread.php?t=948900)

I was having the same problem (HTTP checkouts were fine, HTTPS hung inexplicably) and the linked solution worked for me.

---

### Post by unimatrix on 2011-04-09
Got the same problem. Still no solution :/

---

