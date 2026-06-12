---
title: "Likewise failed install"
date: 2012-09-04
forum: Desktop Environments
---

### Post by itlog on 2012-09-04
Hi all,

I've tried to install likewise on my Ubuntu 12.04 laptop but the installation failed. I've tried to reinstall it and uninstall it with no success.

Here's the output of my "[FONT=&quot]apt-get install -f[/FONT]" and "[FONT=&quot]dpkg --configure -a[/FONT]" commands:


 root@PURB0137:~# apt-get install -f
  Reading package lists... Done
  Building dependency tree
  Reading state information... Done
  0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
  2 not fully installed or removed.
  After this operation, 0 B of additional disk space will be used.
  Setting up likewise-open (6.1.0.406-0ubuntu5) ...
  Error: /usr/sbin/lwsmd --start-as-daemon returned 1 (aborting this script)
   
   
  dpkg: error processing likewise-open (--configure):
    subprocess installed post-installation script returned error exit status 1
  dpkg: dependency problems prevent configuration of likewise-open5:
    likewise-open5 depends on likewise-open; however:
     Package likewise-open is not configured yet.
  dpkg: error processing likewise-open5 (--configure):
    dependency problems - leaving unconfigured No apport report written because the error message indicates its a followup error from a previous failure.
  Errors were encountered while processing:
    likewise-open
    likewise-open5
  E: Sub-process /usr/bin/dpkg returned an error code (1) root@PURB0137:~#
   
   
  root@PURB0137:~# dpkg --configure -a
  Setting up likewise-open (6.1.0.406-0ubuntu5) ...
  Error: /usr/sbin/lwsmd --start-as-daemon returned 1 (aborting this script)
   
   
  dpkg: error processing likewise-open (--configure):
    subprocess installed post-installation script returned error exit status 1
  dpkg: dependency problems prevent configuration of likewise-open5:
    likewise-open5 depends on likewise-open; however:
     Package likewise-open is not configured yet.
  dpkg: error processing likewise-open5 (--configure):
    dependency problems - leaving unconfigured
  Errors were encountered while processing:
    likewise-open
    likewise-open5


How can I get rid of these errors and be able to install it again?

Thanks in advance

GAR

---

