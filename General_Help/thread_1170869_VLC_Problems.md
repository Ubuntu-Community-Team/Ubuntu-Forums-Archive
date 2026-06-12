---
title: "VLC Problems"
date: 2009-05-26
forum: General Help
---

### Post by UglieFrog on 2009-05-26
I need to be able to completeley remove vlc. It needs to be like it was never installed. So I can reinstall it.

The reason for this is i use the pvr function and vlc errors when i forget to turn on the cable box  before I start watching. However i fixed it before
but i was able to reinstall vlc and everything worked again. But now its been a no go. 

So i would like to remove it completeley then try again.

---

### Post by dpsleep on 2009-05-26
try sudo apt-get purge vlc

---

### Post by UglieFrog on 2009-05-26
Thanks for the quick response. It kept my settings. Still didnt work for me. I guess Im going to have to physically remove the card and reinstall it. Unless there is some sort of pci refresh or something. Forgive me Im babblin thank you again for the response Im going to put that command sown in a notebook for future reference

---

### Post by SuperSonic4 on 2009-05-26
```
cp -Rv ~/.vlc ~/.vlc2
```
```
sudo apt-get purge vlc
```
```
rm -Rfv ~/.vlc
```

first code backs up vlc folder
second removes vlc's config files
third removes vlc's settings and it should generate a new one when you load vlc again.

Should that not work and you require your old settings do ```
sudo mv -v ~/.vlc2 ~/.vlc
```

---

### Post by UglieFrog on 2009-05-26
Thank you. I followed youre instructions but still has old settings. Im cursed :)

Do i need to reboot after i enter the terminal settings?

---

### Post by dpsleep on 2009-05-26
what kind of card is it your using? also post the output of lspci.

edit, also i am wondering what is the error that it gives?

---

### Post by UglieFrog on 2009-05-26
00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:09.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:0a.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:0b.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
01:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
07:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)

---

### Post by UglieFrog on 2009-05-26
WinTV-HVR-1600

[http://www.hauppauge.com/site/products/data_hvr1600.html](http://www.hauppauge.com/site/products/data_hvr1600.html)


It used to say failed to initialize but it doesnt any more

ugliefrog@froghq:~$ vlc
VLC media player 1.0.0-rc1 Goldeneye
[0x9c3708] main interface error: no interface module matched "globalhotkeys,none"
[0x9c3708] main interface error: no suitable interface module
[0x888888] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x888888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1

---

### Post by UglieFrog on 2009-05-26
Correction this is what it says


ugliefrog@froghq:~$ vlc
VLC media player 1.0.0-rc1 Goldeneye
[0x9c3708] main interface error: no interface module matched "globalhotkeys,none"
[0x9c3708] main interface error: no suitable interface module
[0x888888] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x888888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
Interface initialization failed
ugliefrog@froghq:~$

---

### Post by dpsleep on 2009-05-26
is it /dev/video0? if so try "cat /dev/video0 > test" and see if you can play that in vlc...

---

### Post by UglieFrog on 2009-05-26
it played the cat file without a problem

---

### Post by dpsleep on 2009-05-26
ok, so in vlc try for "capture mode" video for linux 2

---

### Post by mc4man on 2009-05-26
If there still is an issue vlc 0.9.x and 1.x use ~/.config/vlc to store 2 config files

Starting vlc with ```
vlc --reset-config
```  will reset vlcrc. 

There is also a vlc-qt-interface.conf that can be deleted if need be.

Vlc also maintains a folder in ~/.cache

```
 vlc --reset-plugins-cache
```

---

### Post by UglieFrog on 2009-05-26
Same Error

Interface initialization failed

I bet im going to have to pull card. boot up with out it. power down reinsert then boot up again.

Its some weird glitch. I started it without my cablebox on and everytime taht happens it quits working. Used to be easy fix by just reinstalling vlc but no luck.

Thanks to you and everyone for the help.

---

### Post by UglieFrog on 2009-05-27
Problem solved - Finally got all config files and residuals using the techniques listed on the first page. reinstalled and now im back in biz. Thanks to all. Love the community

---

### Post by rahaman.naik on 2009-11-03
Thanks i followed ur instructions ... it worked for me ... I love this community :)

---

