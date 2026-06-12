---
title: "Hardware BusID changes on every reboot"
date: 2009-06-25
forum: General Help
---

### Post by djhankerd on 2009-06-25
Hi, I have 2 PCIExpress nvidia grafics cards operating 4 monitors... On every reboot my secondary card flips back and forth between PCI Bus ID 6:00.0 and 7:00.0 meaning that I have to restart my comp twice on every reboot to get all 4 monitors working.  I cannot switch slots due to the size of the cards.  Is there any way to either force it to take that resource the same every time or add a duplicate entry into the xorg.conf file?  
I'd try the xorg.conf thing but I'm sick of having the GUI down and having to use nano and figured it'd be quicker to ask... Especially since the optimal solution would be to get the BusID locked in.

---

### Post by dcstar on 2009-06-26
> **djhankerd said:**
> Hi, I have 2 PCIExpress nvidia grafics cards operating 4 monitors... On every reboot my secondary card flips back and forth between PCI Bus ID 6:00.0 and 7:00.0 meaning that I have to restart my comp twice on every reboot to get all 4 monitors working.  I cannot switch slots due to the size of the cards.  Is there any way to either force it to take that resource the same every time or add a duplicate entry into the xorg.conf file?  
I'd try the xorg.conf thing but I'm sick of having the GUI down and having to use nano and figured it'd be quicker to ask... Especially since the optimal solution would be to get the BusID locked in.

Your solution is probably in your BIOS where you may be able to set one card manually rather than have it auto-assign.

---

