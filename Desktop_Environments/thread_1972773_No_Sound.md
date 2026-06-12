---
title: "No Sound"
date: 2012-05-03
forum: Desktop Environments
---

### Post by daimas on 2012-05-03
Fresh install of 12.04 
Sound card points to HDMI and don't have HDMI
Don't know how to change it - I'm a newbie...

3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
penelope@penelope-RC659AA-ABA-a1632x:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
Subdevices: 1/1
Subdevice #0: subdevice #0
penelope@penelope-RC659AA-ABA-a1632x:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.
penelope@penelope-RC659AA-ABA-a1632x:~$ head -n 1 /proc/asound/card*/codec#*

---

### Post by axiom613 on 2012-05-04
Hm, have you checked out the Sound Settings? If you're using Unity, you can click on the volume icon in the top panel, and find the shortcut on the bottom of the menu that pops up.  You should be able to see the output options.  Let me know if that helps.

---

### Post by daimas on 2012-05-06
That box is empty to select a source for sound or mic.
System shows the sound card (3rd to last), but I just don't know how to get it recognized - I'm a newbie getting ready to go back to Winblows...

it's an AMD 64 desktop:


penelope@penelope-RC659AA-ABA-a1632x:~$ lspci
00:00.0 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: NVIDIA Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: NVIDIA Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: NVIDIA Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: NVIDIA Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: NVIDIA Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: NVIDIA Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: NVIDIA Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: NVIDIA Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: NVIDIA Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: NVIDIA Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: NVIDIA Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: NVIDIA Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: NVIDIA Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: NVIDIA Corporation MCP51 PCI Bridge (rev a2)
00:14.0 Bridge: NVIDIA Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 8400 GS] (rev a2)
02:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
03:05.0 FireWire (IEEE 1394): LSI Corporation FW322/323 (rev 70)
03:09.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem

---

