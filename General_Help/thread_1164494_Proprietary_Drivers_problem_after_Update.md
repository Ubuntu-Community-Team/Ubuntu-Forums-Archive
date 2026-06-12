---
title: "Proprietary Drivers problem after Update"
date: 2009-05-19
forum: General Help
---

### Post by felinoel on 2009-05-19
Ubuntu 9.04 now


[QUOTE="Original post"]I had gotten a notification a couple days ago to install some updates, I did, then it told me to restart and after I had it restart my proprietary drivers weren't working, those are for my speakers and screen resolution, now I have no audio and my screen is at 640x480 a size I am way not used to and have a difficult time using due to such; I have tried since then to reinstall them but have failed.

Any thoughts on what my problem could be?[/QUOTE]
Updating the system made it notice the proprietary drivers, but the screen resolution is so small I can't click anything to install these proprietary drivers.

My audio is working fine now, but my old screen resolutions are gone? Its still too tiny to get anything done, which is odd because its the same driver and it worked before? It is NVIDIA accelerated graphics driver version 180, maybe my video card got fried or something?

---

### Post by felinoel on 2009-05-19
At the Volume Control it says it is muted, when I try to unmute it it tells me...> No volume control GStreamer plugins and/or devices found.If that helps for anything

---

### Post by felinoel on 2009-05-20
> **felinoel said:**
> .If I were to try reinstalling Ubuntu, would I be able to just install over the old Ubuntu and leaving my data as it is, or would I have to move all my data to somewhere else because installing a new Ubuntu wipes the computer?

---

### Post by paradigm2 on 2009-05-20
I wouldn't reinstall over this as someone should be able to help you fix it. :)

Which packages did you install?

Go to System -> Administration -> Log File Viewer

and select dpkg.log and cut and paste the last ten or so lines.

also I guess you might as well post the output of 

```

lspci

```

Which will give us your basic hardware info.

---

### Post by felinoel on 2009-05-20
> **paradigm2 said:**
> I wouldn't reinstall over this as someone should be able to help you fix it. :)

Which packages did you install?

Go to System -> Administration -> Log File Viewer

and select dpkg.log and cut and paste the last ten or so lines.

also I guess you might as well post the output of 

```

lspci

```

Which will give us your basic hardware info.I see no "Log File Viewer," perhaps "System Log" instead? No I don't see any dpkg there...

As for the lspci...```
michael@michael-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
03:08.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
03:09.0 Communication controller: Conexant HSF 56k Data/Fax Modem
03:0a.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)

```

---

### Post by QIII on 2009-05-22
Could you go go System -> Admin -> Hardware Drivers and let us know if a proprietary driver is available?

---

### Post by felinoel on 2009-05-22
> **QIII said:**
> Could you go go System -> Admin -> Hardware Drivers and let us know if a proprietary driver is available?

That was the first thing I did when the problem first appeared, but just because I just now tried it again and still nothing, which is odd because they used to be there...

---

### Post by felinoel on 2009-05-23
> **felinoel said:**
> That was the first thing I did when the problem first appeared, but just because I just now tried it again and still nothing, which is odd because they used to be there...

I even tried removing the volume control packages and reinstalling them but still nothing

---

### Post by 3rdalbum on 2009-05-23
How were your proprietary drivers installed in the first place?

If they were installed from Hardware Drivers, then they should keep up-to-date with your kernel and not cause this problem.

If you manually installed them, i.e you downloaded them from a website, then you will need to recompile and/or reinstall them every time you update your kernel.

---

### Post by felinoel on 2009-05-23
> **3rdalbum said:**
> How were your proprietary drivers installed in the first place?

If they were installed from Hardware Drivers, then they should keep up-to-date with your kernel and not cause this problem.

If you manually installed them, i.e you downloaded them from a website, then you will need to recompile and/or reinstall them every time you update your kernel.
Definitely positive I installed them from Hardware Drivers, but if I can do it from a website doing it every time I update my kernel is fine, how do I find out what drivers I need?

And its either this or just install the new Ubuntu over this... because my Hardware Drivers isn't noticing them anymore and if I wipe it clean with a brand new OS it might wake up and notice it...

Or should I try removing the Video and Sound cards and putting them back in? Maybe they got jarred loose? But at the same time and exactly after I install an update?

---

### Post by Legace on 2009-05-24
Try to remove your nvidia drives with EnvyNG: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by felinoel on 2009-05-24
> **Legace said:**
> Try to remove your nvidia drives with EnvyNG: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Ok..? What did that do?

---

### Post by felinoel on 2009-05-24
Oh I see, now I can change it to different resolutions, but the highest is still 640x480, it gave me smaller choices?

---

### Post by felinoel on 2009-05-28
> **felinoel said:**
> I could just install the new Ubuntu over this... because my Hardware Drivers isn't noticing them anymore and if I wipe it clean with a brand new OS it might wake up and notice it...

Or should I try removing the Video and Sound cards and putting them back in? Maybe they got jarred loose? But at the same time and exactly after I install an update?

.

---

### Post by felinoel on 2009-06-02
Updating the system made it notice the proprietary drivers, but the screen resolution is so small I can't click anything to install these proprietary drivers.

---

### Post by felinoel on 2009-06-02
My audio is working fine now, but my old screen resolutions are gone? Its still too tiny to get anything done, which is odd because its the same driver and it worked before? It is NVIDIA accelerated graphics driver version 180, maybe my video card got fried or something?

---

