---
title: "Dell Poweredge 2950 III"
date: 2008-10-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cjkeeme on 2008-10-09
I am minutes away from purchasing a Dell Poweredge 2950 III to run as a terminal server.  I have attached an image of the proposed purchase.

Can anyone tell me if everything will be compatible with my LTSP installation of Ubuntu 8.04?  I am particularly concerned about the hard drive controller and the network adapter.  Thank you. 

[IMG]http://www.keeme.net/files/2950.jpg[/IMG]

---

### Post by linux_tech on 2008-10-09
Looks like there are linux drivers available for the nic and controller.   

linux drivers for the NIC
[http://www.broadcom.com/support/ethernet_nic/netxtremeii.php](http://www.broadcom.com/support/ethernet_nic/netxtremeii.php)

SAS drivers for PERC 6 RAID controllers are included in kernel.org 2.6.x kernels

For a tool to monitor your raid controller you should try Megacli
You can download it from the LSI website:
[http://www.lsi.com/support/downloads/megaraid/miscellaneous/linux/1.01.4](http://www.lsi.com/support/downloads/megaraid/miscellaneous/linux/1.01.4)
0_Linux_Cli.zip

---

### Post by astarmathsandphysics on 2008-10-13
I am trying to install ubuntu 7.10 on a swapdisk in a dell poweredge 1900.. It installs but refuses to boot from the swap disk, sayin"error loading operating system" Any ideas?

---

### Post by bcalder01 on 2008-10-16
Hey Linux_Tech, think you could update that link so that it works? 

TIA!

---

### Post by astarmathsandphysics on 2008-10-17
> **astarmathsandphysics said:**
> I am trying to install ubuntu 7.10 on a swapdisk in a dell poweredge 1900.. It installs but refuses to boot from the swap disk, sayin"error loading operating system" Any ideas?

I read someone that you should do a windows parttion on the same disk. Have done this but now it boots to the network.

---

