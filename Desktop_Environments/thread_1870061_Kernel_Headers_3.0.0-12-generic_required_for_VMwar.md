---
title: "Kernel Headers 3.0.0-12-generic required for VMware Workstation 6.5.5"
date: 2011-10-26
forum: Desktop Environments
---

### Post by richardOracleDba on 2011-10-26
I'm having a problem installing VMware Workstation 6.5.5 into Ubuntu 11.10

The message I get says:

"Before you can run VMware Workstation, several modules must be compiled and loaded into the running kernal
Kernel Headers 3.0.0-12-generic

Kernel headers for version 3.0.0-12-generic were not found....."

It gives me the option of pointing the installer to the headers.  I can see the following in /usr/src:


drwxr-xr-x 24 root root 4096 2011-10-13 23:42 linux-headers-3.0.0-12
drwxr-xr-x  7 root root 4096 2011-10-13 23:42 linux-headers-3.0.0-12-generic

Sadly, when pointing the installer at these it says:

"C Header files matching your running kernel were not found...."

Can anyone offer a solution or way forward?

Thanks.

---

### Post by gsmanners on 2011-10-26
This seems apropos: [http://www.vmware.com/support/product-support/workstation.html](http://www.vmware.com/support/product-support/workstation.html)

---

