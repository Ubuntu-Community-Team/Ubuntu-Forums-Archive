---
title: "Power Consumption for Ubuntu 10.04"
date: 2012-03-31
forum: Desktop Environments
---

### Post by kifcaliph on 2012-03-31
Hi

I use Ubuntu on a home PC and I observed that the fan runs faster than Windows 7, and it get noisy. I tried to close many apps on Ubuntu to see if it's going to slow or not, the result it slows but it goes back to run faster when I open any application even if I am only browsing simple pages , it's not like Windows 7. In Windows 7, I barely hear the processor's fan when I leave the pc on idle state. so is there a way to manually manage power consumption and idle state in Ubuntu

---

### Post by jonnyboysmithy on 2012-03-31
What hardware are you on?

---

### Post by kifcaliph on 2012-03-31
I am using Intel Core 2 Duo E6320 1.86GHz, with the latest linux kernel update of Ubuntu 10.04

---

### Post by jonnyboysmithy on 2012-03-31
Do you know what the graphic card is? And have you installed any proprietary driver for it?

Try using powertop to identify what process is using so much power.
In a terminal run:
```

sudo apt-get install powertop-1.13 
```And then run it:
```

sudo powertop-1.13 
```

---

### Post by kifcaliph on 2012-03-31
these are the results:


Top causes for wakeups:
  45.6% (238.9)   [kernel scheduler] Load balancing tick
  22.0% (115.4)   [uhci_hcd:usb5, HDA Intel, nvidia] <interrupt>
   9.0% ( 47.0)   USB device  5-2 : Usb Mouse (SIGMACHIP)
   5.7% ( 29.8 )   desktopcouch-se
   1.0% (  5.4)D  beam.smp
   2.9% ( 15.0)   [eth0] <interrupt>

---------------------------------------------------------------
Top causes for wakeups:
  37.4% (119.7)   [kernel scheduler] Load balancing tick
  27.4% ( 87.5)   [uhci_hcd:usb5, HDA Intel, nvidia] <interrupt>
   9.3% ( 29.9)   desktopcouch-se
   3.1% ( 10.0)   [ata_piix] <interrupt>
   3.1% ( 10.0)   ubuntuone-syncd
   3.1% ( 10.0)   gnome-system-mo
------------------------------------------------------------
Top causes for wakeups:
  34.6% (124.5)   [kernel scheduler] Load balancing tick
  31.3% (112.7)   [uhci_hcd:usb5, HDA Intel, nvidia] <interrupt>
   8.3% ( 29.9)   desktopcouch-se
   7.3% ( 26.2)   USB device  5-2 : Usb Mouse (SIGMACHIP)
   2.8% ( 10.0)   [ata_piix] <interrupt>
   2.8% ( 10.0)   ubuntuone-syncd

---

### Post by jonnyboysmithy on 2012-03-31
Seems pretty much normal. It could be that the graphics card is having a hard time.
I have a laptop with a ATI card in it. The open source drivers ran really hot. Fans on all the time. Finally I disabled the ATI card alltogether and switched to integrated. That solved the over heating.
Thats the only thing I can think of.

Have you checked if there is a proprietary driver available? 
Top left on the tool bar: >System>Administration>Additional Hardware Drivers

---

### Post by Dr_Rohin on 2012-04-13
What's your complete setup

---

