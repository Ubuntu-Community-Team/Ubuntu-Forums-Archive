---
title: "12G DELL R820 will not boot after 12.04 64bit LTS Install"
date: 2012-06-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jhickey on 2012-06-28
We recently purchased a new DELL R820.  This is one of the new 12th Generation servers.

The install of 12.04 64bit server edition installs with any issues.  The only packaged we added is ssh.  

After the install on reboot the server hangs and will either reboot and/or panic.

I've included the specs below.  Does anyone see any suspect hardware on the list.  We also purchased several R620 and Ubuntu loads without issue on those servers.  

High Level Specs (yes this is a monster)
4xIntel Xeon E5-4640 2.40GHz 512GB RAM

**Detailed specs for the R820 are below:**

 1 225-2607 PowerEdge R820
 1 430-4426 Broadcom 5719 QP 1Gb Network Interface Card, Low Profile
 1 342-1413 VFlash, 8GB SD Card for iDRAC Enterprise
 1 421-5339 iDRAC7 Enterprise
 1 430-4418 Broadcom 5720 QP 1Gb Network Daughter Card
 1 342-0615 SAS 6Gbps HBA External Controller
 1 331-6543 2.5" Chassis with up to 16 Hard Drives
 1 331-5685 RAID 1 for H710p, H710, H310 Controllers
 1 342-4049 PERC H710p Adapter RAID Controller, 1GB NV Cache
 1 317-9328 2x Intel Xeon E5-4640 2.40GHz, 20M Cache, 7.2GT/s QPI, Turbo, 8 Core, 95W, Max Mem 1600MHz
 1 331-6161 Heat Sink for PowerEdge R820
 1 317-9332 DIMM Blanks for Systems up to 4 Processors
 1 317-9336 Upgrade to Four Intel Xeon E5-4640 2.40GHz, 20M Cache, 8.0GT/s QPI, Turbo, 8C, 95W
 1 331-6161 Heat Sink for PowerEdge R820
 1 331-6162 PWA for PowerEdge R820
 32 317-9640 16GB RDIMM, 1600 MHz, Standard Volt, Dual Rank, x4
 2 342-0847 600GB 10K RPM SA SCSI 6Gbps 2.5in Hotplug Hard Drive
 1 313-7541 DVD ROM, SATA, Internal
 1 331-4607 Dual, Hot-plug, Redundant Power Supply (1+1), 1100W


FYI here are the working R620 specs
Pretty much the same system just a lower amount of RAM and only dual processor.

  225-2108 PowerEdge R620
  331-4761 PowerEdge R620 Shipping - 4/8 Drive Chassis
  430-4426 Broadcom 5719 QP 1Gb Network Interface Card, Low Profile
  342-1413 VFlash, 8GB SD Card for iDRAC Enterprise
  421-5339 iDRAC7 Enterprise
  430-4418 Broadcom 5720 QP 1Gb Network Daughter Card
  342-3660 SAS 6Gbps HBA External Controller, Low Profile
  331-4823 Cable for Mini PERC Cards for Chassis with up to 8 Hard Drives
  342-3666 Chassis with up to 8 Hard Drives and 3 PCIe Slots
  331-4224 RAID 1 for H710P/H710/H310 (2 HDDs)
  342-3531 PERC H710P Integrated RAID Controller, 1GB NV Cache
  317-8585 Intel Xeon E5-2665 2.40GHz, 20M Cache, 8.0GT/s QPI, Turbo, 8C, 115W, Max Mem 1600MHz
  331-4762 Heat Sink for PowerEdge R620
  317-8460 Intel Xeon E5-2665 2.40GHz, 20M Cache, 8.0GT/s QPI, Turbo, 8C, 115W
  317-8688 DIMM Blanks for Systems with 2 Processors
  331-4762 Heat Sink for PowerEdge R620
  317-9640 16GB RDIMM, 1600 MHz, Standard Volt, Dual Rank, x4
  342-0847 600GB 10K RPM SA SCSI 6Gbps 2.5in Hotplug Hard Drive
  318-1390 DVD ROM, SATA, Internal

---

### Post by mishnz on 2012-07-08
Hi,

We're looking at purchasing a DELL R820.
The vendor has tested this for us and his coming up against the same issue.

Did you make any progress with this?

---

### Post by jhickey on 2012-07-09
Currently no and we were up against a bit of a deadline so we ended up going with RHEL which does not seem to have an issue.

We did notice there was a BIOS update a few days back but we were not able to test Ubuntu 12.04 with it.

As a side note 11.10 64bit Server installs and runs without issue so my guess is that it was something to do with the 3.2 vs 3.0 kernel.

Best of luck

---

### Post by sral on 2012-08-13
I installed Ubuntu 12.04 on a R820 with similar specs and ran into the same issue. My first idea was to boot from CD (grml in my case), chroot into the installed Ubuntu and apt-get update; apt-get dist-upgrade.

This worked out just fine and the system boots now, so the issue seems to have been fixed in a kernel update. But I guess with 12.04.1 coming this week it will work OOTB as it should.

HTH,

Lars

---

### Post by jhickey on 2012-08-13
Thanks for the update.  I think we tried upgrading but it was probably before it was patched.

---

### Post by create123 on 2013-03-20
Sorry to revive an old thread but did you ever get 12.04 up and running on these?  I have a few R620 and have been running 12.04 successfully except for the additional Broadcom 5719QP card.  I can not get it to send any traffic through.

---

