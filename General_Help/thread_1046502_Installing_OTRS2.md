---
title: "Installing OTRS2"
date: 2009-01-21
forum: General Help
---

### Post by supanatral on 2009-01-21
When I try to install OTRS on my ubuntu box, I get an error at the end saying:
> Creating config file /etc/apache2/conf.d/otrs2 with new version
This module does not exist!
dpkg: error processing otrs2 (--configure):
 subprocess post-installation script returned error exit status 1
processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing
 otrs2
E: Sub-process /usr/bin/dpkg returned an error code (1)

I've been trying to get this to work for a few hours with endless googling but I can't seem to figure it out. Has anybody installed otrs on ubuntu?

---

### Post by ehorton on 2009-02-10
I actually have a production OTRS2 server running on Ubuntu server.  It is version 2.2.7.  I used the package manager to install.  Worked fine.  I am now in the process of trying to figure out the upgrade to the latest version.

---

