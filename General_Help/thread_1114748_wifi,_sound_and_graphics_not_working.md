---
title: "wifi, sound and graphics not working"
date: 2009-04-03
forum: General Help
---

### Post by john@proficientpc on 2009-04-03
im a newbe at this but i cant seem to figure out how i lost my nvidia drivers and also my wifi card is not registering and also i have no sound drivers it all happen after i installed virtual box plez help!!!

---

### Post by Dejai on 2009-04-03
Questions:
1. What Version of Ubuntu are you using.
2. Is it the open source virtual box, or is it the proprietary one.
3. Are you running Ubuntu in Virtual box? Or Virtual box in Ubuntu. 

I would like to find a bit more out about your hardware to help diagnose the problem:
Applications->Accessories->Terminal 

Type:
```
sudo lspci | grep Network
```
```
sudo lspci | grep VGA
```

If either does not return anything you can always post:
```
sudo lspci
```

Recommendations: 
Check System-Administrator->Hardware Drivers and see if Nvidia is enabled.

---

### Post by john@proficientpc on 2009-04-03
yeah the card does not appear in hardware drivers and im running vbox in Ubuntu 8.04 it's the vbox you can install from add/remove programs in applications also i had to dl a different kernel in synaptic

---

### Post by Dejai on 2009-04-03
I know that Virtual Box does download a kernel module but as to this effecting your systems graphics card and wireless card I am slightly stumped. Maybe some permissions have changed... Try adding yourself as a normal user to the vbox group.. System->Administrator->Users and Groups. (You should do this anyway otherwise you won't have access to anything when using VBox printers etc.) 

It may also be worth uninstalling the application, seeing if it then works and possibly installing the proprietary version instead. I have to admit I am slightly perplexed by the issue. The commands I asked you to run would help a lot thanks. Run the commands with both sudo and without it. 

I don't recommend it but you could logging in as root from gdm, only temporarily and test if wifi is working from there.

---

### Post by john@proficientpc on 2009-04-03
i don't know what happen i have to hit esc and in grub go to Ubuntu generic heres sudo lspci info 


00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:05.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:05.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
01:06.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:06.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

---

### Post by john@proficientpc on 2009-04-03
im just going to reinstall Ubuntu 8.04

---

### Post by 3rdalbum on 2009-04-03
Please, don't start two threads for the same problem. I have replied in your other thread.

---

