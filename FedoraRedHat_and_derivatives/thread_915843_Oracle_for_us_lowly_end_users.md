---
title: "Oracle for us lowly end users?"
date: 2008-09-10
forum: Fedora/RedHat and derivatives
---

### Post by igknighted on 2008-09-10
So... In several of my classes we are using Oracle 10g, and I have been forced to use Windows for these classes as the copy we were given was the windows installer.  Also, most of our work is done in SQL Developer.  But the load of running an Oracle DB and SQL Developer is a lot for my laptop... is there any way to install an Oracle DB onto my Fedora server at home that I could log into?

---

### Post by Coombabah on 2008-09-11
> **igknighted said:**
> So... In several of my classes we are using Oracle 10g, and I have been forced to use Windows for these classes as the copy we were given was the windows installer.  Also, most of our work is done in SQL Developer.  But the load of running an Oracle DB and SQL Developer is a lot for my laptop... is there any way to install an Oracle DB onto my Fedora server at home that I could log into?

Check this out to see if it is what you want.

You don't need the version on that CDROM as you can download versions that run on linux from Oracle.com instead.

[http://www.oracle.com/technology/products/database/xe/index.html](http://www.oracle.com/technology/products/database/xe/index.html)

Oracle 10g Express edition may be close enough for what you want and it is also free. The free version is limited to only using 1GB of RAM, 1 CPU and 4GB disk space with an upgrade path to the paid version if you later decide you need a beefier database. You can have more RAM CPUs and hard drive space but that's all it will use. Should still be heaps for what you want.

I run it in Ubuntu 8.04 under vmware for development and it actually seems slightly faster than our production servers at work.
Just make sure you have a large enough swap partition if you don't give it much ram or it won't install. I don't work mine that hard and find 2GB swap and 512MB ram OK.

I also have it running on my laptop, a Lenovo 3000 C200 (a cheap but good value low end laptop) and haven't noticed it running slower just takes a few seconds longer to boot.
You may be able dual boot your laptop and install Oracle under Ubuntu if you have the hard drive space and enough ram.

Get the rpm to install it under Fedora or the tar for Ubuntu.
There's lots of information around to help with the install.

---

