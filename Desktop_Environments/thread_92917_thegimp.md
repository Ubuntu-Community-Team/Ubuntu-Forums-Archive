---
title: "thegimp"
date: 2005-11-20
forum: Desktop Environments
---

### Post by akurashy on 2005-11-20
Preconfiguring packages ...
(Reading database ... 84599 files and directories currently installed.)
Unpacking libgimp2.0 (from .../libgimp2.0_2.2.8-2ubuntu6_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libgimp2.0_2.2.8-2ubuntu6_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libgimp-2.0.so.0', which is also in package gimp
Errors were encountered while processing:
 /var/cache/apt/archives/libgimp2.0_2.2.8-2ubuntu6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Ok this is what happened, I did a deb package of gimp 2.3.5 i went, first message was that it couldn't overwrite the libgimp, then i removed and reinstalled libgimp package, i tried to install my gimp deb package but it gives me the same error. about libgimp.2.0. etc etc. 

how can i fix this?

---

### Post by kperkins on 2005-11-20
"sudo dpkg --force-overwrite <name-of>.deb"
Lose the quotes when you type it in.

---

