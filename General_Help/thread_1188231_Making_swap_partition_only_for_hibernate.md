---
title: "Making swap partition only for hibernate"
date: 2009-06-15
forum: General Help
---

### Post by nusch on 2009-06-15
While I've instaling the system on my 4GB RAM laptop I didn't create swap partition, but now I need it for hibernate. Is there a way to create a swap partition but prevent all "ubuntu automagic detectors" from activating it for normal usage ? I very rarely use more than 3GB of RAM and second reason is I/O on disk which cost some battery life so I would rather to keep ubuntu only use physical memory and swap for hibernate. How to do this ?

---

### Post by sdennie on 2009-06-15
You would need to resize your partition to make room for the swap first (You can use gparted from the install CD to do this easily).  Then just treat it as normal swap but put the following into /etc/sysctl.conf:

```

vm.swappiness = 0

```

That will prevent linux from actually using the swap unless it absolutely must use it.  A more extreme option would be to not mount the swap at boot time but put a script in /etc/pm/sleep.d that mounts it just before a hibernate starts and unmounts it after the thaw.  I'm not sure if that would work and the swappiness setting is probably just as good.

---

