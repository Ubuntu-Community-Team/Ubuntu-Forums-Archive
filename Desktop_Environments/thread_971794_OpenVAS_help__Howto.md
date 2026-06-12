---
title: "OpenVAS help / Howto?"
date: 2008-11-05
forum: Desktop Environments
---

### Post by brimmer on 2008-11-05
Hey I'm running 8.10 Ibex and installed the openVAS client and server packages but I can't get run any of the server commands to make a certificate or create a user.  Can someone tell me how to get openVAS to work?

---

### Post by tinyforks on 2008-11-10
I get multiple dependency errors when trying to install from Synaptic or from apt (via command line).  

How did you install?

---

### Post by tinyforks on 2008-11-10
I get multiple dependency errors when trying to install from Synaptic or from apt (via command line).  

How did you install?

---

### Post by brimmer on 2008-11-12
Are you running the latest version of ubuntu?  I just used -apt and it installed no problem.  I just can't get it configured

---

### Post by tinyforks on 2008-11-12
Yes.  8.10, fully patched.  It wants several lib files.

---

### Post by syklops on 2009-01-18
I just install OpenVAS from source and had no problems whatsoever.

Can you post up the output of your commands, and the errors you got and I should be able to point you in the right direction.

---

### Post by BinaryEnCoder on 2010-02-26
it has a right sequence to install it
uninstall all the things than dont work, then do this simple steps:


first download the right packages
wget [http://wald.intevation.org/frs/download.php/595/openvas-client-2.0.4.tar.gz](http://wald.intevation.org/frs/download.php/595/openvas-client-2.0.4.tar.gz)
wget [http://wald.intevation.org/frs/download.php/561/openvas-libnasl-2.0.1.tar.gz](http://wald.intevation.org/frs/download.php/561/openvas-libnasl-2.0.1.tar.gz)
wget [http://wald.intevation.org/frs/download.php/600/openvas-libraries-2.0.3.tar.gz](http://wald.intevation.org/frs/download.php/600/openvas-libraries-2.0.3.tar.gz)
wget [http://wald.intevation.org/frs/download.php/607/openvas-manager-0.6.1.tar.gz](http://wald.intevation.org/frs/download.php/607/openvas-manager-0.6.1.tar.gz)
wget [http://wald.intevation.org/frs/download.php/588/openvas-plugins-1.0.7.tar.gz](http://wald.intevation.org/frs/download.php/588/openvas-plugins-1.0.7.tar.gz)
wget [http://wald.intevation.org/frs/download.php/593/openvas-server-2.0.2.tar.gz](http://wald.intevation.org/frs/download.php/593/openvas-server-2.0.2.tar.gz)

then install them in this order
1. openvas-libraries
2. openvas-libnasl
3. openvas-server
4. openvas-plugins

just untar, configure, make, make install

then you just follow the instructions , create a certificate , create a user then you run
openvas-nvt-sync and will work just fine , it woked for me

---

