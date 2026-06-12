---
title: "Kernel and Xorg updates"
date: 2013-02-04
forum: Desktop Environments
---

### Post by ranger12 on 2013-02-04
Hi all, I have updated to kernel 3.50 on Desktop 12.04.1(As well as my server, also running 12.04.1 - well it says 12.04.2 now.) and now there is an update to the old 3.2 kernel. 

Question: if I tell Update Manager to update the old 3.2 kernel will it configure the system to boot with that updated 3.2 kernel or will it still boot with the 3.5 kernel?

The question on Xorg is what is the lts quantal package I use in Software Center to pull in everything I need like with the lts quantal kernel? Would it be **xserver-xorg-lts-quantal**? I just noticed that if you install this package it is by default checked to suck in and install the lts-quantal kernel. I guess I did it backwards maybe.

Have a great week everyone.

---

### Post by ranger12 on 2013-02-05
Okay forget the first question.  That was probably a stupid question. I should have figured it would be smart to boot off the latest version kernel. I upgraded the old 3.2 kernel on my server and rebooted. It still boots off the 3.5 kernel. I still am wondering about the correct xorg quantal package in software center though.

---

### Post by ranger12 on 2013-02-14
Okay, I should have figured it would have been as simple s this:

sudo apt-get install xserver-xorg-lts-quantal

Rebooted the machine and all seems to be fine so far.

---

