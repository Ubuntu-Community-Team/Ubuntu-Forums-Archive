---
title: "Dell - ubuntu server edition 10.4 LTS won't boot"
date: 2011-01-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by spurk on 2011-01-24
Hello,

Im trying to install ubuntu server edition but everytime i reboot after the installation i get the following error message:

Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
-Check rootdelay= (did the system wait long enough?)
-Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules: ls /dev)

ALERT! /dev/disk/by-uuid/46b14a60-7fc4-487c-487c-a6a5-a9d66889dab7 does not  exist. Dropping to a shell

(initramfs)


My disk is setup like this:
 1. / = primary 2. /var = logical 3. /home = Logical 4. SWAP = Swap

And the grub is installer on master drive as recommended.
The server specs is listed under. 
Any suggestions on how i should proceed?

PowerEdge R310 Chassis, Up to 4
Cabled Hard Drives and Quad Pack
LED diagnostics
 
Components
1 Intel Core I3 530 2.93GHz, 4M Cache, 2C/4T
1 1U Rack Bezel
1 8GB Memory (4x2GB Single Rank UDIMMs) 1333MHz
2 146GB SAS 15k 3.5" HD Cabled
1 SAS 6iR Controller for Cabled HDD Chassis
1 16X DVD-ROM Drive SATA with SATA Cable
2 2M Rack Power Cord C13/C14 12A
1 Redundant Power Supply (2 PSU) 400W
1 iDRAC6 Embedded BMC
1 Sliding Ready Rack Rails
1 C10 Cabled - R1 for SAS 6iR or PERC H200/H700, Exactly 2 SAS/SATA Cabled Drives

---

### Post by spurk on 2011-01-25
I can type exit from the initramfs tho and that brings me to the user login where the server works just fine.
Any way to skip this fauly message so its safe to reboot the server without being infront of it in RL and type exit?

---

### Post by spurk on 2011-01-25
Changing the timeout too 60 worked fine.
Case closed.

---

### Post by spurk on 2011-01-25
Changing the timeout too 60 worked fine.
Case closed.

---

### Post by ramasan on 2011-07-06
I have an R310 with H700 RAID controller and I cannot get it installed. Upon successful installation, reboot, I get
Out of disk
grub rescue

Using guided install of whole disk (6 TB).

Incidentally, ESXi 4.1 installs out of the box fine.

Any suggestions? Did you need to do anything special to get it to install?

---

### Post by spurk on 2011-10-17
> **ramasan said:**
> I have an R310 with H700 RAID controller and I cannot get it installed. Upon successful installation, reboot, I get
Out of disk
grub rescue

Using guided install of whole disk (6 TB).

Incidentally, ESXi 4.1 installs out of the box fine.

Any suggestions? Did you need to do anything special to get it to install?

Edit */etc/default/grub*
add *rootdelay=xx* to this line:
GRUB_CMDLINE_LINUX_DEFAULT="**rootdelay=60** quiet splash"

then exec: sudo *update-grub*

---

