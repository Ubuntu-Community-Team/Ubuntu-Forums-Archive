---
title: "random mouse freeze"
date: 2009-05-20
forum: General Help
---

### Post by analogman128 on 2009-05-20
System setup is:
Mythbuntu Intrepid 8.10 (i.e. Xubuntu) 64-bit
AMD Phemon 8650 Toliman Tri-Core 2.3GHz
Asus M3N78-EM Motherboard (GeForce 8300)
NVIDIA Driver 180.22
Netgear WG311T Super-G Wireless PCI
AirStar-HD5000 ATSC/8VSB HDTV PCI Tuner Card
LG BD/HD DVD 16x DVD+/- RW GGC-H20LK
Vidabox USB RF Wireless Keyboard with Integrated Trackball

I've been fighting this bug for months, and it's still there.  This is my MythTV box.  I use a wireless keyboard/trackball combo to control it from the couch.  Every few days the trackball cursor will freeze. I've tried restarting the X server, unloading/reloading the usbhid module, and pretty much every other suggestion I could find on the web.  But nothing short of a reboot will bring it back to life.  I see the same behaviour in Gnome. 

The rest of the system keeps running fine, including  the wireless keyboard (physically attached to the trackball and on the same wireless receiver).  I now keep another wired USB mouse plugged in so I can shut down cleanly after a freeze; the wired mouse never freezes.

This problem used to be MUCH worse before I added "noapic" to the boot options.  The cursor would freeze within 30 seconds of a reboot, always while moving.  I don't really know what noapic does, but it helps.  I've also noticed freezes are more frequent if I have a USB thumb drive plugged in.  I updated my BIOS about a month ago and haven't noticed any difference.  I tried "acpi=force" and "irqpoll" boot options, but they didn't help.

How can I figure out what's causing this?  Output from dmesg (right after a freeze) is attached; I didn't notice anything suspicious.  I think this freeze happened when I had a thumb drive plugged in.  Are there other system logs that will shed some light on the problem?  Some process I can try restarting?

---

