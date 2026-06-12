---
title: "Slow Desktop Menu on UNR 9.04"
date: 2009-04-24
forum: Desktop Environments
---

### Post by CombinedEffort on 2009-04-24
I'm running 9.04 from a USB stick on an eee 701 and the Menu/Desktop that shows when the machine first boots is VERY laggy - almost unusable.

Applications such as firefox are fine, but moving the mouse around the Menu/Desktop is like I'm using a remote machine over a 56k connection.

Anyone else getting this on an eee 701? I'm trying to wean the out-laws off WinXP...

Cheers,

Rich

---

### Post by tonyr1988 on 2009-04-24
It should run faster if you install it to disk vs. booting from USB drive (I'm on a Dell Mini 9 and it sped up). Also, have you looked into eeebuntu? It's Ubuntu specifically designed for eees.

---

### Post by CombinedEffort on 2009-04-24
> **tonyr1988 said:**
> It should run faster if you install it to disk vs. booting from USB drive (I'm on a Dell Mini 9 and it sped up). Also, have you looked into eeebuntu? It's Ubuntu specifically designed for eees.

I don't think it's a USB .vs. disk issue - the stick has an 'access light' and it doesn't appear to be accessing the stick when I see the lag.

I wanted to avoid going for a fork ubuntu distro, but that may be the best option...

Rich

---

### Post by dj.dule on 2009-04-24
I installed 9.04 NBR on EEEpc 1000's hard disk, fresh install and have the same problem. It is running from hard disk. So I doubt it is USB issue.

---

### Post by blokeley on 2009-04-25
I have created a bug for this:
[https://bugs.launchpad.net/ubuntu/+bug/366562](https://bugs.launchpad.net/ubuntu/+bug/366562)

---

### Post by brunogirin on 2009-04-25
I confirm the same problem on my EeePC 701 (installed on disk, not USB)

---

### Post by brunogirin on 2009-04-25
Looks like there is a related bug already reported: [https://bugs.launchpad.net/netbook-remix-launcher/+bug/239943](https://bugs.launchpad.net/netbook-remix-launcher/+bug/239943)

---

### Post by njpatel on 2009-04-27
Hi guys, this is an issue with the Intel drivers that are in Jaunty (and the kernel module that handles them). The bug is at [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/349314](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/349314), where you'll also find an updated kernel package which should fix the issue for you. 

I believe that we're trying to get this into -updates as an SRU asap too.

---

### Post by warren94 on 2009-05-03
All you need to do,, however silly it sounds, is choose generic in grub **NOT** the default server edition.
hope this helps.

---

