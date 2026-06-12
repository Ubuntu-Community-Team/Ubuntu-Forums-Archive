---
title: "K3b no longer works with kernel upgrade"
date: 2009-06-20
forum: General Help
---

### Post by olympic on 2009-06-20
Greetings. Following a recent update (from 2.6.28.11-generic to 2.6.28.13-generic - Ubuntu Jaunty Jackalope) K3b no longer runs except as "root".

I have checked another hard drive which has kernel .11-generic and k3b works fine.  I have tried a re-install through apt-get and also through <System><Admin><Synaptic Package Manager> and the installation appears to be okay (comparing installed files with those on the hard drive with .11-generic kernel).

By the way, the "update" of the kernel came about through the "Update manager".  I only became aware of it after I turned the laptop back on and found I had two extra items in grub (I have a dual boot with WinXP - cannot get Flight Simulator 2002 running in Linux)

Any thoughts?

---

### Post by dcstar on 2009-06-20
> **olympic said:**
> Greetings. Following a recent update (from 2.6.28.11-generic to 2.6.28.13-generic - Ubuntu Jaunty Jackalope) K3b no longer runs except as "root".
.......

K3B works fine on my updated system using the -13 kernel.

---

### Post by olympic on 2009-06-21
Hi dcstar.

Problem solved.

Needed "sudo chown -R <username>:<username> ~/.kde"

Cheers

---

