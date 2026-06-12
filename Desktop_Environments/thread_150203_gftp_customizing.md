---
title: "gftp customizing"
date: 2006-03-25
forum: Desktop Environments
---

### Post by gymsmoke on 2006-03-25
I'm nost sure exactly where this question falls, so I thought I'd start here.
I found an article which tells how to re-install gftp with ssl/tsl.  The instructions were for an older version of debian, and I'd like someone more experienced than me to tell me if this will work ok, or if there is anything else I might need in order for this to work properly with Ubuntu 5.10.

apt-get build-dep gftp 
apt-get install libssl-dev
apt-get source gftp 
edit the call to ./configure in debian/rules 
dpkg-buildpackage -rfakeroot

Any input is greatly appreciated.  I need to have an ftp client which uses ssl/tsl authentication.

---

