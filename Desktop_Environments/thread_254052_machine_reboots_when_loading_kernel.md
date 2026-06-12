---
title: "machine reboots when loading kernel"
date: 2006-09-09
forum: Desktop Environments
---

### Post by gsrcobr on 2006-09-09
Hi,

I have just installed an Ubuntu Server in my old home server.
It's a AMD K6-II 300Mhz, 96MB SDRAM, Quantum 4.3GiB hard drive and a PC-CHIPS motherboard.

Installation runs fine, but after that, at first reboot,
machine gets into a loop.

Grub menu appears, but when linux starts loading kernel,
the machine reboots. Neither normal and rescue modes works.

Someone could help me?

PS: Conectiva (up to 10) and Fedora Core (up to 3) runs fine on this machine.

Thanks,

---

### Post by numa666 on 2006-09-28
Same problem here:

reboots when it starts loading kernel.

ISO was dowloaded yesterday.

AMD K6-2 475 MHz, 128mb RAM, 4Gb HDD

Other problem I noticed is that the setup didnt recognize my NICs : 2x RT2500 and 1x Ethernet card.

Ideas would be appreciated :-)

---

### Post by lamego on 2006-09-28
The Server CD version installs a kernel version which has been reported to not work with some old hw.
The possible solutions are:
  - Reinstall the system using the Alternate CD with the minimal install option.
  - Boot from the CD with the recovery option and install the 386 kernel, and boot from it.

---

