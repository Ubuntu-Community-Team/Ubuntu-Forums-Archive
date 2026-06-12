---
title: "Can't install MySQL on ubuntu 9.04"
date: 2009-05-25
forum: General Help
---

### Post by pavsid on 2009-05-25
Hi,

I'm having trouble with MySQL on my Ubuntu machine.  It stopped working a few days ago (couldn't start) and so i tried reinstalling it but getting this error everytime i try to install it:

E: /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10_amd64.deb: subprocess pre-installation script returned error exit status 1

Really don't know what's wrong - can anyone help?

---

### Post by pavsid on 2009-05-25
Ok, i have narrowed it down to the fact that i had altered my datadir for mysql. I think this has caused a problem since upgrading to Jaunty as things worked just fine before.

Anyway, reinstalling LAMP with default settings works fine, however as soon as i try to change the mysql datadir (in both my.cnf and apparmor.d/usr.sbin.mysl) then i cannot restart mysql.  I have chown of the new dir to mysql and chmod to 755, so i don't think it's a permissions issue.

This must be something to do with the way Jaunty handles with things.

Anybody got any ideas?

---

### Post by pavsid on 2009-05-25
was permissions after all....!

---

