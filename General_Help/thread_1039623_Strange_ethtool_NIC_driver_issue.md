---
title: "Strange ethtool NIC driver issue"
date: 2009-01-14
forum: General Help
---

### Post by brendancaulfield on 2009-01-14
Hey Everyone,

I am having a strange issue. I am using Hardy on an HPDL360 with an on-board Broadcom Nextreme II (5708).  I recently downloaded and installed the latest driver (1.7.6b) for this card and it seems to be working great.  Unfortunately, upon reboot, ethtool -i eth0 reports the wrong driver version (and hence disallows settings available in the new driver).  What is really weird is that modinfo reports the information associated with the new driver.  See below for details:

root@host:~# ethtool -i eth0
driver: bnx2
version: 1.6.9
firmware-version: 1.9.6
bus-info: 0000:03:00.0

root@ohost:~# modinfo bnx2
filename:       /lib/modules/2.6.24-22-server/kernel/drivers/net/bnx2.ko
version:        1.7.6b
license:        GPL
description:    Broadcom NetXtreme II BCM5706/5708/5709 Driver
author:         Michael Chan <mchan@broadcom.com>
srcversion:     F524C3FF338F5CE8E76A837
alias:          pci:v000014E4d0000163Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00001639sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016ACsv*sd*bc*sc*i*
alias:          pci:v000014E4d000016AAsv*sd*bc*sc*i*
alias:          pci:v000014E4d000016AAsv0000103Csd00003102bc*sc*i*
alias:          pci:v000014E4d0000164Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000164Asv*sd*bc*sc*i*
alias:          pci:v000014E4d0000164Asv0000103Csd00003106bc*sc*i*
alias:          pci:v000014E4d0000164Asv0000103Csd00003101bc*sc*i*
depends:        
vermagic:       2.6.24-22-server SMP mod_unload 
parm:           disable_msi:Disable Message Signaled Interrupt (MSI) (int)

It appears that the system is actually using the new driver but I am unable to use ethtool to change some required settings.

Anyone ever seen this?  Any and all ideas are appreciated.

Thanks,

-brendan

---

### Post by brendancaulfield on 2009-01-14
All,

I think I have resolved this issue.  Apparently ethtool was not ushowing latest driver information because I had not updated the initramfs.  I ran an *update-initramfs -u* and the problem went away.

Thanks and I hope this helps someone out there,

-brendan

---

