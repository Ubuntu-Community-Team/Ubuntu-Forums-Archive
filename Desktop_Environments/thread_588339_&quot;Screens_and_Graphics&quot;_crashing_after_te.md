---
title: "&quot;Screens and Graphics&quot; crashing after testing Radeon driver"
date: 2007-10-23
forum: Desktop Environments
---

### Post by Can+~ on 2007-10-23
Specs:
-Graphics card: ATI Radeon X800 GTO2 (430).
-MOBO: Asus A8N-SLI
-Sound: Integrated
-cpu: AMD Athlon 64 3700+.
-Screen: LG1752S
...

Here is the "lspci > ~/Desktop/asdf":
```
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)
01:00.1 Display controller: ATI Technologies Inc R430 [Radeon X800 XL] (PCIe) (Secondary)
05:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
```

I don't want to start with the "In feisty ...", but I must: In feisty Beryl worked like a charm, I used the default driver (radeon driver I think), and enabled AIGLX. Now in gutsy (32 bit), the only driver that has worked for me is the VESA driver. FGLRX doesn't want to boot, but this is not an issue.

When opening "Screens and Graphics", driver section and select the "Ati Radeon" driver, then "test", the screen turns black for a few seconds and return the window closes, jumping back to the VESA driver.

I don't care about having the Eq:demo running, or whatever (since I use wintendows for that (definition: having windows just for games)). I mainly want to run some opengl sutff, have wobbling windows and particulary, I miss the exposé-like effect T_T. So in short terms:

-What I should do to start the radeon driver?
-Is the radeon driver the one by default in feisty, right?
-If it isn't possible to run any of them, how do I enable Aiglx with another driver?

Hope I made myself clear, since my mother language is Spanish.

---

### Post by Can+~ on 2007-10-23
bump.

*[OMG NEW FGLRX WITH AIGLX!]("http://www.phoronix.com/scan.php?page=article&item=887&num=1")* gonna try that now.

No luck with the new FGLRX, I still have the same problem with it:
-After ubuntu loads and xorg kicks in, instead of anything useful, I get 15 or so Vertical Green Lines, and 3 red lines with a black background. Looks like xorg recognizes the error, and reloads 3 times, then fires up the Failsafe.

With "Ati" driver, I get nothing.
"Radeon" won't start.

*last edit*
OMG! I fixed it changing the refresh rate, for some reason, FGLRX screwed it up badly! YAY!

---

