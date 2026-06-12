---
title: "The right source for Kismet???"
date: 2005-09-09
forum: Desktop Environments
---

### Post by daller on 2005-09-09
Hi All,

On my own laptop, with an IPW2100 it was pretty simple to setup Kismet (uses the orinoco-source)

But what about this network-card?

0000:00:09.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)

Something is also not right with the managed-driver:

0000:00:09.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)

RUNNING IWLIST: (eth0 is the one!)

oskar@oskar:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      Interface doesn't support scanning : Operation not supported

sit0      Interface doesn't support scanning.

---

### Post by daller on 2005-11-23
Just to sign this thread as closed!

---

