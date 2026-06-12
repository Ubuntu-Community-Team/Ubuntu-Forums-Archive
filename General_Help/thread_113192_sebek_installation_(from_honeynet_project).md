---
title: "sebek installation (from honeynet project)"
date: 2006-01-05
forum: General Help
---

### Post by cyracks on 2006-01-05
Hi,

I have problems installing sebek on ubuntu 5.10. When trying to configure sebek I get the following error:
configure: error: Cannot find  /lib/modules/2.6.12-10-386/build/net/packet/af_packet.c.

Searching for af_packet.c in [http://packages.ubuntu.com/](http://packages.ubuntu.com/) didn't produce any results.

#uname -a returns
... 2.6.12-10-386 ... 

packages linux-source-2.6.12, linux-headers-2.6.12-10 and linux-headers-2.6.12-10-386 are installed but that doesn't help.

Any ideas ?

regards

---

### Post by cyracks on 2006-01-05
The solutin was just to copy af_packet.c from kernel source to /lib/modules/2.6.12-10-386/build/net/packet/

regards

---

