---
title: "HELP &gt;&gt; removing alien converted packages that did not uninstalled properly"
date: 2009-01-04
forum: General Help
---

### Post by user-max on 2009-01-04
Hello all.
I am running Ubuntu 8.10.
I recently ran into a problem that I needed to install VMware-Server.
Initially, I downloaded an .rpm and converted it to .deb via alien.
Since then, I had to remove it and install newer version of VMware-Server.
This time around I found .deb package and when I try to install it it gives me the following output:



max@armaggedon:~/Desktop/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware Server has been detected.

The previous installation was made by the rpm installer (version 3).

Converting the rpm3 installer database format
        to the tar3 installer database format.

You have a product that conflicts with VMware Server installed.  Continuing
this install will first uninstall this product.  Do you wish to continue?
(yes/no) [yes] yes

error: package VMware-server is not installed
Uninstall failed.  Please correct the failure and re run the install.

Execution aborted.


Help is greatly appreciated.

---

### Post by dcstar on 2009-01-04
> **user-max said:**
> Hello all.
I am running Ubuntu 8.10.
I recently ran into a problem that I needed to install VMware-Server.
Initially, I downloaded an .rpm and converted it to .deb via alien.
Since then, I had to remove it and install newer version of VMware-Server.
This time around I found .deb package and when I try to install it it gives me the following output:
........
Help is greatly appreciated.

Go into the package manager and remove it as you would with any .deb package.

---

### Post by user-max on 2009-01-04
> **dcstar said:**
> Go into the package manager and remove it as you would with any .deb package.

Thank you for prompt reply. The problem is that I have removed that package with aptitude remove cvar. However, I suspect that somehow it was not removed properly and that is preventing me from installing new vmware server.

---

