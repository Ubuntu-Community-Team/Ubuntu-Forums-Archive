---
title: "PowerEdge T410 Dual Onboard NIC"
date: 2009-08-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by doc_777 on 2009-08-25
Hey everyone. We have a new Dell power edge T410  server here and I really wanted to put Ubuntu Server on it... but so far it has been difficult to get along with. :popcorn:

The installer would not recognize the SATA DVD drive and failed with "No common CDROM drive found".  I got on past this by installing from a external USB DVD drive.  During the installation it failed to find the network card but completed anyway.  I now have a booting system and sitting at the command prompt, but no network as of yet. This system has a dual interface, on motherboard, NIC.

lshw -C network shows 2 x  broadcom controllers "UNCLAIMED"

lspci shows 2 x "Broadcom Corporation Unknown Device 163b (rev 20)"

I have tried modprobe tg3 and modprobe bnx2 but have not had any luck yet getting the interface to actually come up.

Has anyone any tips for this? I would change the network card but do not have any PCI eXpress NICs around at the moment and this system has no PCI slots...  Help!  :confused:

---

### Post by doc_777 on 2009-08-25
Solved:  I was trying to use the 8.04 server edition LTS release so it would last a few years.  But not much of the hardware was recognized.  I downloaded the 9.04 X64 edition and it recognizes everything.  The DVD drive, the RAID and the NIC.  I will just use it and be happy.  ( I think it is the newer kernel )  :P

---

