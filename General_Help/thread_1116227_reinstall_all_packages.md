---
title: "reinstall all packages"
date: 2009-04-04
forum: General Help
---

### Post by steeler on 2009-04-04
i need to reinstall all packages due to harddisk corruption
aptitude reinstall ~i fails saying it cannot locate linux-headers-2.6.24-21.

i'm only able to boot into command line
any help appreciated

---

### Post by ibuclaw on 2009-04-04
Before you can download any packages, you must be connected to the internet.

If the option isn't listed for **Root Terminal with Networking** in the Recovery Mode options, then enter just the plain "**Root Terminal**" and switch to runlevel 4
```
init 4
```
Login as normal user, and get connected via there. (Ethernet cable connection to your modem/router is preferable).

Regards
Iain

---

