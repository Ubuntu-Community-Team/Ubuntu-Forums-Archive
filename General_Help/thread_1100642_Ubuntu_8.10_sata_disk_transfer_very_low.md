---
title: "Ubuntu 8.10 sata disk transfer very low"
date: 2009-03-19
forum: General Help
---

### Post by TMachado on 2009-03-19
I'm installed and reinstalled Ubuntu 8.10 many times, but always I had the same problem: sata data transfer is very slow on my Toshiba A210-ac. I've search but cant find any solution.

Any ideas?

---

### Post by kryptikos on 2009-03-19
Curious...install systat (aptitude install sysstat) and then run:

(as root or sudo)  **iostat -x 5 sda  **   (replace sda with whatever your device is) while you are doing your data transfer.

Also what does **hdarm -I /dev/sda**(again replace sda with your disk device assignment) say?

I noticed in launchpad there is a bug listed:
[https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/262845]("https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/262845") but not sure what kernel you are using.

---

### Post by TMachado on 2009-03-20
> **kryptikos said:**
> Curious...install systat (aptitude install sysstat) and then run:

(as root or sudo)  **iostat -x 5 sda  **   (replace sda with whatever your device is) while you are doing your data transfer.

Also what does **hdarm -I /dev/sda**(again replace sda with your disk device assignment) say?

I noticed in launchpad there is a bug listed:
[https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/262845]("https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/262845") but not sure what kernel you are using.

I have a lot of information when I run that command. What to you want to know exactly ?

My kernel is 2.6.27-11-generic.

---

