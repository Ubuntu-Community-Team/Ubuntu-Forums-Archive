---
title: "Duplex printing in OpenOffice.org2"
date: 2006-03-24
forum: Desktop Environments
---

### Post by Guizzy on 2006-03-24
I have problem saving Duplex printing as default in OpenOffice.org; it always get back to single page.

The printer in question is a Imagistics im4510, and I it used to keep the setting until I changed the printer's IP address. Not only doesn't it keep the duplex setting for the current printing, but I have to manually tell OpenOffice (though the printer configuration) that the printer is indeed equipped with the duplex module.

I've tried about everything; from modifying the PPD so that the "Duplex module installed" is default to changing cups configuration files by hand.

What are the different configuration files that could override my choices? Is there something I'm missing?

Thank you in advance.

---

### Post by John Jason Jordan on 2006-03-24
[QUOTE=Guizzy]I have problem saving Duplex printing as default in OpenOffice.org; it always get back to single page.[/QUOTE]
I have similar problems printing to Laserjet 5SiMx and Laserjet 8000DN printers. Features on the printers are not even listed. And it continually forgets the settings that I have checked as defaults.

I suspect that OO.o 2.0x is not CUPS enabled. Actually, I have 1.93.129, because I use 64-bit Ubuntu Breezy and that's the latest version that is available in Synaptic. But I'll hazard a guess that 2.02 is not CUPS enabled either. Either that, or OO.o is not seeing everything that CUPS sees, or is ignoring some of the features, or something. Whatever the cause of the problem, it sucks. I hope someone can tell me that I'm wrong and how to correct the problem.

---

### Post by Guizzy on 2006-03-27
I doubt it is simply because Oo2 doesn't support CUPS well; it worked perfectly before I changed the printer's IP.

My guess is that multiple programs are modifying different configuration files, one which I don't know about is having priority over the rest.

---

