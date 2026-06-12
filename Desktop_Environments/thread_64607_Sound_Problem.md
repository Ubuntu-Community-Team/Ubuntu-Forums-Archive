---
title: "Sound Problem"
date: 2005-09-11
forum: Desktop Environments
---

### Post by rmckayfleming on 2005-09-11
Hi, I'm pretty new to the Linux world and I've been having problems with my sound card, Ubuntu doesn't detect it and I just want my sound. My system is a PII 400Mghz
128MB Ram, 10GB hard drive. I dont know what sound card I have because I got the system second hand. I had Windows 2000 on it but not anymore. Please help me. Thanks. :???:

---

### Post by cwaldbieser on 2005-09-11
[QUOTE=rmckayfleming]Hi, I'm pretty new to the Linux world and I've been having problems with my sound card, Ubuntu doesn't detect it and I just want my sound. My system is a PII 400Mghz
128MB Ram, 10GB hard drive. I dont know what sound card I have because I got the system second hand. I had Windows 2000 on it but not anymore. Please help me. Thanks. :???:[/QUOTE]
Try posting the output of:
```
$ lspci
``` 
If your card is a detected PCI card, it should show up in there.

---

### Post by rafakl on 2005-09-11
As cwaldbieser suggested, use lspci, and then search for anything with the word "sound" or "audio" on it and post the result here.

 :-P

---

### Post by rmckay on 2005-09-12
Here are the results. I had to get new account cause my password was messed up. I know what it was but the forums say otherwise.

ryan@LinuxBox:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0a.0 SCSI storage controller: Adaptec AHA-7850 (rev 01)
0000:00:0b.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 86C326 5598/6326 (rev c3)

Nothing about audio.

---

### Post by rmckay on 2005-09-13
Hello can anybody help.

---

