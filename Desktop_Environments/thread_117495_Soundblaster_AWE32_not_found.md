---
title: "Soundblaster AWE32 not found"
date: 2006-01-15
forum: Desktop Environments
---

### Post by kubcat on 2006-01-15
I have read most of the threads on getting the AWE32 cards to work. Most of them have to do with entries in the config file. However, running pnpdump results in no card found. It is set up as a dual boot PC, and running in windows XP, the card works fine. It is a PnP ISA soundcard, and in windows the IRQ is 7. I have tried setting the BIOS to reserve the irq, memory and DMA settings exactly as they are shown under windows, but it doesn't work. I am running a tyan trinity 100AT motherboard with Award PnP BIOS.

The only clue I have is that once upon a time under windows it conflicted with the motorola wireless card (a PCI card) on IRQ 5, and both wouldn't work at the same time. I honestly can't remember why they both started working under windows, but they do now. 
I don't want to spend any money on this machine, so upgrading the soundcard is out - especially since I know the h/w combo does work. Its a point of pride, now! Any help??

---

### Post by Mr_Grieves on 2006-01-15
Checked this page out?
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+64+Value.&chip=sb16%2C+emu8000&module=sbawe](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+64+Value.&chip=sb16%2C+emu8000&module=sbawe)

Or.. this little guide:
[http://www.linux.com/howtos/Soundblaster-AWE-4.shtml](http://www.linux.com/howtos/Soundblaster-AWE-4.shtml)

Do you got ALSA installed?

---

