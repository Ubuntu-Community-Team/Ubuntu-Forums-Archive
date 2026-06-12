---
title: "QUIET, SPLASH and BOOT"
date: 2007-11-03
forum: Dell  Ubuntu Support
---

### Post by stef56 on 2007-11-03
QUIET, SPLASH and BOOT
On my dell latitude D810 boot takes almost 180 seconds with the two mains steps :.

[ 23.053414] EXT3-fs: mounted filesystem with ordered data mode.
[ 119.249610] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

[ 128.606263] EXT3 FS on sda5, internal journal
[ 152.632762] input: Lid Switch as /class/input/input5

i should notice that during the boot sequence Usplash doesn't appear

If I delete SPLASH and QUIET instructions in the boot, boot time is 60 seconds
But the recording events obtained with DMESG are totally different and of course Ubuntu splash doesn't appear.

Does anyone is able to explain the relation between SPLASH, QUIET, boot time and how to optimize the boot sequence ?

Thanks,

Stef

---

### Post by bluedragon436 on 2007-11-04
[http://ubuntuforums.org/showthread.php?t=580903&highlight=slow+boot]("http://ubuntuforums.org/showthread.php?t=580903&highlight=slow+boot")

Check out the above post it should help you out if not use the search function and do a search for slow boot, cause I had this same issue when I first installed 7.10 on my computer and this was able to fix it for me....Hope it helps and welcome!!!

---

