---
title: "help sound problem"
date: 2007-05-08
forum: Desktop Environments
---

### Post by therealmkb on 2007-05-08
im a quite new to linux only used it for a few days before so very basic use i have a problem i recently installed ubuntu 6.10 and i cant get the sound to work its a on board sound control belived to be a nforce mpc or mcp i forget which 1 

some one told me to do this i hope it helps
lspci
00:00.0 Host bridge: nVidia Corporation nForce CPU bridge (rev b2)
00:00.1 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
00:00.2 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
00:00.3 RAM memory: nVidia Corporation nForce 420 Memory Controller (DDR) (rev b             2)
00:01.0 ISA bridge: nVidia Corporation nForce ISA Bridge (rev c3)
00:01.1 SMBus: nVidia Corporation nForce PCI System Management (rev c1)
00:02.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
00:03.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
00:04.0 Ethernet controller: nVidia Corporation nForce Ethernet Controller (rev              c2)
00:08.0 PCI bridge: nVidia Corporation nForce PCI-to-PCI bridge (rev c2)
00:09.0 IDE interface: nVidia Corporation nForce IDE (rev c3)
00:1e.0 PCI bridge: nVidia Corporation nForce AGP to PCI Bridge (rev b2)
02:00.0 VGA compatible controller: nVidia Corporation NVCrush11 [GeForce2 MX Int             egrated Graphics] (rev b1)

i have tried a few things but non seem 2 work

---

### Post by therealmkb on 2007-05-08
and i juz realised this is posted in the wrong place sorry

---

### Post by jocko on 2007-05-08
I don't see any audio controller in your lspci output.
Are you sure you copied the complete output?
Does "lspci | grep audio" say anything?

---

