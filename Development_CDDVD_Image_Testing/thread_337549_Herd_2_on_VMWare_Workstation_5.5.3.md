---
title: "Herd 2 on VMWare Workstation 5.5.3"
date: 2007-01-13
forum: Development CD/DVD Image Testing
---

### Post by tomranson on 2007-01-13
Hi all,

I was hoping to install Herd 2 on VMWare Workstation 5.5.3 (running on a Ubuntu 6.10 host)- I am using the alternate install CD for Herd 2, rather than the live CD.

The installer starts and commenced hardware detection, and then drops back to the blue screen with no text displayed, and stays like this indefinately.

Alt+F4 reveals "Jan 13 12:19:34 kernel: not found.". This message repeats indefinately also.

Any ideas people? :-?

---

### Post by spd106 on 2007-01-13
I'm getting the same symptoms on Virtual PC 2004. I also get some other messages 

kernel: [  904.023433] Intel ISA PCIC probe: not found
main-menu[2854]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
main-menu[2854]: DEBUG: resolver (ext2-modules): package doesn't exist (ignored)
main-menu[2854]: DEBUG: resolver (fat-modules): package doesn't exist (ignored)
main-menu[2854]: DEBUG: resolver (firmware-modules): package doesn't exist (ignored)
main-menu[2854]: INFO: Falling back to the package description for console-setup-udeb
main-menu[2854]: INFO: Menu item 'netcfg' selected

plus some dhclient messages...

It comes up with network autoconfiguration failed at one point, but then goes back to detecting hardware.

It does make progress, but it's taken nearly 30 mins to get to the partitioner. I know virtualisation is supposed to be slow, but this is laughable. I should be half way through the install by now. Dapper wasn't nearly this slow.

---

### Post by twisted_steel on 2007-01-14
Herd 2 installation worked fine for me using VMware Server 1.0.1 under Edgy.  I used the regular install CD (feisty-desktop-i386) and didn't have any problems once I changed the memory to 256MB.  The default settings for 'Ubuntu' are 160MB, which can run the installer, but it won't get past selecting a time zone (if I recall correctly, it needs at least 192MB).  After restarting, X came up properly, with the network working as well (I have mine set to NAT).

---

