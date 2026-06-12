---
title: "MySql-Server 5.0 broken?"
date: 2009-03-19
forum: General Help
---

### Post by nkonstas on 2009-03-19
Hello,

I tried to install mysql on a brand new Toshiba NB100 notebook and I get the following error:

/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable

at which point the installation fails with

 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1) 

This is a known bug as reported here: 
[https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.0/+bug/316594](https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.0/+bug/316594)

...but I cannot find any resolution or workaround. I desperately need to install mysql - please help!

Cheers,
Nikos.

---

### Post by kryptikos on 2009-03-19
The easiest work around is to just install MySQL directly.

[http://dev.mysql.com/downloads/mysql/5.1.html#linux]("http://dev.mysql.com/downloads/mysql/5.1.html#linux")

Follow the instructions from MySQL, they are fairly detailed and pretty well written. Remember that the repositories are great for quick installations, but you still are running Linux, so you can add software that doesn't live in the repositories :)

---

### Post by nkonstas on 2009-03-24
Thank you - did that.

I want to install packages that depend on mysql (like mantis). How do I prevent apt-get/synaptic from trying to install mysql...?

Cheers,
Nikos.

---

