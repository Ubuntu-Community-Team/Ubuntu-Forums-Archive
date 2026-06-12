---
title: "PHP not working in home directory after upgrade"
date: 2010-05-10
forum: Desktop Environments
---

### Post by dldeskins on 2010-05-10
I am having a problem with my PHP installation.  After I upgrade to 10.04 (64 bit), the PHP quit working in my home directory... that is:
/home/username/public_html/
or
[http://localhost/~username/](http://localhost/~username/)

When the PHP is called, the dialogue comes up to download and I am able to download the intact PHP file. The *.html files work normally in the home directory.

The /var/www/ directory with PHP works normally (phpMyAdmin, etc.).    

What am I missing?

Thanks.

---

### Post by dldeskins on 2010-05-11
What could be causing this?

---

### Post by dldeskins on 2010-05-11
OK, I have found out that this is a bug on ubuntu server 10.04:

[http://www.mail-archive.com/ubuntu-server-bugs@lists.ubuntu.com/msg30620.html](http://www.mail-archive.com/ubuntu-server-bugs@lists.ubuntu.com/msg30620.html)

but I have this bug also on the desktop version.

The workaround listed does not work for me.

---

