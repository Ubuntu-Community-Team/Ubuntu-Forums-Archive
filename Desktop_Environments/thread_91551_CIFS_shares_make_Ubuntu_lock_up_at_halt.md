---
title: "CIFS shares make Ubuntu lock up at halt"
date: 2005-11-17
forum: Desktop Environments
---

### Post by joenix on 2005-11-17
Hi,

I have the following problem: I'm mounting some CIFS shares over a wireless network. When shutting down, the wireless network gets shut down before the shares are unmounted. When they get unmounted afterwards, Ubuntu locks up.
I tried changing /etc/rc0-6/S31unmountnfs.sh to S00unmountnfs.sh, but the shares still don't get unmounted first.
Any suggestions?
Thanks,
Jeroen

---

