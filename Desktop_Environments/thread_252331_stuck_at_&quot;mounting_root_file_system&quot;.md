---
title: "stuck at &quot;mounting root file system&quot;"
date: 2006-09-06
forum: Desktop Environments
---

### Post by tommiller on 2006-09-06
I have a strange problem.

I had ubuntu running on my desktop for atleast 3 months with no problems. I tried to enable XGL on my Radeon 9900 last week with no apparent problems. But then after a few reboots over a few days, the X Server would not start. Eventually, I tried to re-install Ubuntu on the same machine from scratch. 

So, 

1. I reformatted the partition
2. Installed Ubuntu from the Live CD.
3.  No USB or SATA
4. Boot up from hard drive gets stuck at "Mounting root file system"

I restart the system, and in the Boot options I use "boot:rescue acpi=off" and the system boots up.

What is the issue here? Anyone else with the same problem?

---

### Post by mgmiller on 2006-09-06
I had a similar problem where the machine would hang at the same point, mounting root file system.  I even went so far as to unplug my harddrive and just try booting from the live CD and I had the same problem.  It turned out one on the PCI cards (USB/Firewire card) had gotten "confused" and was causing the problem.  I removed it and it booted fine.  I reinserted it and it has worked fine since.  Try removing all pci cards and rebooting.  Then plug them back in (with the power off, of course), and reboot again.  This will force the BIOS to redetect and reset the hardware.  You can also try changing the acpi settings in your bios.  While you're in there, disable legacy USB support while you're at it.  It can cause all sorts of weird things to happen to modern USB devices.

---

### Post by tommiller on 2006-09-08
Most of what I have is built in, I have just an AGP card. I removed the card and put it back. I restarted the system and things came back up. I reconnected my SATA drive and then tried booting up. It was stuck again at "Mounting root file system". I went through the exercise of removing everything and putting them back and things began working. What confuses me the most is the fact that I had the same SATA drive working on Ubuntu for at least a couple of months.

Thanks for your suggestion, it helped.

---

### Post by FakeOutdoorsman on 2006-09-08
I got the same error: "mounting root file system".  Or maybe it said "waiting for root file system".  Anyway, I installed Ubuntu with one SATA drive.  After installation I added a sata NTFS drive and got the errors when it was plugged in.  All I did was switch the sata ports for each drive and then it worked.  What I mean is drive 0 was in sata port a, and drive 1 was in port b when I was getting errors.  I fixed it by putting drive 0 into port b and drive 1 into port a.

---

