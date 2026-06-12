---
title: "PCI SATA controller affects GRUB"
date: 2008-05-25
forum: Desktop Environments
---

### Post by Urbancrow on 2008-05-25
HI
Here is the situation

IBM 300PL 6594A3U Computer
2 IDE drives
Floppy
CD drive
DVDRW connected to a Silicon Image 3114 PCI SATA host controller with bios flashed to IDE.

I have UBUNTU with GRUB installed on 1st primary drive and Win 98 on second drive. When I select Win 98 from Grub menu, at stage 1.5 I get error 21 and system halts. If I remove the SATA card from the system Grub loads windows as advertised.

Can anyone please help

Thanks :)

---

### Post by meierfra. on 2008-05-25
I don't really understand what is going on, but I suggest to  make sure that W98 drive is second in the boot order in the bios.

---

### Post by Urbancrow on 2008-05-26
Hi,
My Problem is solved, I reinstalled the PCI SATA controller card into a different PCI slot and rebooted, everything works fine. I am not sure why, I think it has something to do with sharing the same IRQ with video which is passed control from the mobo bios. Just a guess Thanks to everyone who replied.

Urbancrow:)

---

