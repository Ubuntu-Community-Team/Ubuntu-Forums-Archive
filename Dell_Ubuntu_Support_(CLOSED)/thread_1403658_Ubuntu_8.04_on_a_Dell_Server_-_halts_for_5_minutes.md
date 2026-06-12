---
title: "Ubuntu 8.04 on a Dell Server - halts for 5 minutes every day different time"
date: 2010-02-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Mitek on 2010-02-10
Hello,

we run Ubuntu 8.04 LTS Server Edition on the following hardware

Dell PE R710 2*Xeon X5560 2.8GHz,6x4GB(1333MHz),6*450GB(15), DVD+/-RW,C5,PERC 6/i,Dual NetXtreme 5709,iDRAC6 Exp,High Output PSU Redund(2PSU)870W,Bezel,Riser with 1PCIe x16+2PCIe x4,2x PowCords, Chassis for Up to 6x 3.5",

We use Mysql 5.5, Apache, PHP, Nginx, Sphinx. Daily traffic is about 50000 visitors.

Once in a while the server becomes inaccessible - requests take very long to process or timeout completely. During these slowdowns it is possible to login to the server using ssh. Top command halts - doesn't show anything. PS command works ok. Munin shows a white space on the CPU graph during these intervals - please see attached. I looked through syslog but found nothing special there. Swapping is turned off using swapoff -a. The problem happens once in a while, sometimes during the night when there's no high load, sometimes several times a day. Sometimes we don't see it for couple full days.

I upgraded firmware in the server to the lastest versions and it did not help.

Where do I start the investigation?

---

### Post by Mitek on 2010-02-10
UPD: During blackout it is not possible to login to the server, but existing ssh consoles work. I found another thread on the same problem here
[http://ubuntuforums.org/showthread.php?t=1343083](http://ubuntuforums.org/showthread.php?t=1343083)

---

### Post by sciric on 2010-02-10
> **Mitek said:**
> UPD: During blackout it is not possible to login to the server, but existing ssh consoles work. I found another thread on the same problem here
[http://ubuntuforums.org/showthread.php?t=1343083](http://ubuntuforums.org/showthread.php?t=1343083)

I believe the problem is kernel related. There must be a problem with  Ubuntu 8.04 LTS on Dell R710.

We recently upgraded the kernel (manually compiled) to 2.6.32.7 and the  freezes since then have gone.

---

### Post by forumID on 2010-07-27
Please help get this fixed. See bug report at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/607167](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/607167)

---

