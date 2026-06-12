---
title: "Odd fsck/fstab problem with UPS and USB drive"
date: 2009-04-07
forum: General Help
---

### Post by prupert on 2009-04-07
Hi

I haven't been able to find much about this online, so thought I should post here.

I have a rather odd problem.

I have a Fujitsu server running Ubuntu 8.04. It has two internal SATA drives and 1 external USB2.0 Hard drive that has its own power supply.

All drives are mounted via /etc/fstab.

All was working fine until I started using a UPS (Uninterutable Power Supply) and apcupsd.

If I have the USB hard drive plugged into one of the UPS sockets, the server fails during boot with a fsck error that says it couldn't find the USB hard drive listed in /etc/fstab, it then drops to a basic shell. If I manually continue booting via CTRL+D it all works fine and the USB drive is mounted as it should be.

If I have the USB drive plugged into a normal AC power socket, everything boots as normal.

For some reason fsck doesn't see the USB drive when it is plugged into the UPS power supply, even though the UPS is plugged into the mains.

Just to clarify, I am not trying to boot the system on the UPS's battery backup power, I am booting it with the UPS plugged in to AC power, so it should be the same as when plugged directly into AC power.

apcupsd is loaded via an init.d script.

Anyone ever heard of anything like this?

Is apcupsd interfering with fsck or /etc/fstab?

Anyone have any ideas where I can look for the reason fsck can't see the USB drive. I have looked in /var/log/fsck/ logs, but all it says is the process died because the drive /dev/sdc1 was not found....

Any views on this appreciated.

FYI, I would like the hard drive to also be on the UPS since it is my backup drive, so that if power is lost, data isn't lost if the drive was being written to.

---

