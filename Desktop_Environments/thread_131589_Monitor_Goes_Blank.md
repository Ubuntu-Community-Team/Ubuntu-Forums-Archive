---
title: "Monitor Goes Blank"
date: 2006-02-16
forum: Desktop Environments
---

### Post by reb68 on 2006-02-16
I am using Breezy badger 5.10 and KDE 3.5. A few days ago my screen started going blank after a few hours. I can turn the monitor off and back on and all is well. Could this be the Monitor or the video card. I do not know how to find out which type I have or I would list it here. Is there a way to list hardware or periphiels?

---

### Post by nalmeth on 2006-02-16
You can use the terminal with this command:
lspci

Or go into SYSTEM --> ADMINISTRATION --> DEVICE MANAGER

Is the monitor set for standby or something?

SYSTEM --> PREFERENCES --> SCREENSAVER ?

---

### Post by reb68 on 2006-02-16
I never had it set to standby. I have had to reboot to get the monitor to show. I wonder if it is the Monitor going out.

---

### Post by reb68 on 2006-02-16
This is what terminal shows. Does this help?
dick@dick:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:0e.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
0000:00:0f.0 USB Controller: OPTi Inc. 82C861 (rev 10)
0000:00:10.0 Communication controller: Conexant: Unknown device 10b4 (rev 89)
0000:00:12.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 05)
0000:00:14.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:14.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:14.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:14.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)
dick@dick:~$

---

