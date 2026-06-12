---
title: "Minecraft + Linux = Problems (SOS)"
date: 2013-07-06
forum: Gaming &amp; Leisure
---

### Post by SmartGoober on 2013-07-06
I have Linux Ubuntu 12.04... Went to [www.minecraft.net]("http://www.minecraft.net") and downloaded  minecraft. Then I noticed, "The jar is executable and should work as-is,  also please use Oracle's JVM." Then I went into the termanal and typed  the following commands...

[COLOR=#ff0000]sudo add-apt-repository ppa:webupd8team/java[/COLOR]
[COLOR=#ff0000]sudo apt-get update[/COLOR]
[COLOR=#ff0000]sudo apt-get install oracle-java7-installer[/COLOR]

Then to confirm, I typed the folling command...

[COLOR=#ff0000]java -version[/COLOR]

It replyed...

[COLOR=#ff0000]java version "1.7.0_25"
Java&#8482; SE Runtime Environment (build 1.7.0_25-b15)
Java HotSpot&#8482; 64-Bit Server VM (build 23.25-b01, mixed mode)[/COLOR]

Then I assumed that it was all installed correctly. I went back to my  desktop, right clicked on Minecraft.jar, and click "Open With Oracle  Java 7 Runtime".  Up came the new minecraft launcher. On the bottem  right hand conner I logged in with my minecraft account that I payed  for. Then it said, "Welcome, DuhGoober". I click play, it popped up a  black window. Then it created a Crash Report...

[COLOR=#ff0000]---- Minecraft Crash Report ----
// Oops.

Time: 7/6/13 2:31 PM
Description: Initializing game

java.lang.RuntimeException: org.lwjgl.LWJGLException: X Error - disp:  0x7f086042fa90 serial: 159 error: GLXBadRenderRequest request_code: 154  minor_code: 1
    at org.lwjgl.opengl.Display.update(Display.java:648)
    at org.lwjgl.opengl.Display.update(Display.java:628)
    at atn.R(SourceFile:505)
    at atn.O(SourceFile:328)
    at atn.d(SourceFile:598)
    at net.minecraft.client.main.Main.main(SourceFile:101)
Caused by: org.lwjgl.LWJGLException: X Error - disp: 0x7f086042fa90  serial: 159 error: GLXBadRenderRequest request_code: 154 minor_code: 1
    at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(LinuxDisplay.java:318)
    at org.lwjgl.opengl.LinuxContextImplementation.nSwapBuffers(Native Method)
    at org.lwjgl.opengl.LinuxContextImplementation.swapBuffers(LinuxContextImplementation.java:79)
    at org.lwjgl.opengl.ContextGL.swapBuffers(ContextGL.java:175)
    at org.lwjgl.opengl.DrawableGL.swapBuffers(DrawableGL.java:90)
    at org.lwjgl.opengl.Display.swapBuffers(Display.java:618)
    at org.lwjgl.opengl.Display.update(Display.java:646)
    ... 5 more


A detailed walkthrough of the error, its code path and all known details is as follows:
---------------------------------------------------------------------------------------

-- Head --
Stacktrace:
    at org.lwjgl.opengl.Display.update(Display.java:648)
    at org.lwjgl.opengl.Display.update(Display.java:628)
    at atn.R(SourceFile:505)
    at atn.O(SourceFile:328)

-- Initialization --
Details:
Stacktrace:
    at atn.d(SourceFile:598)
    at net.minecraft.client.main.Main.main(SourceFile:101)

-- System Details --
Details:
    Minecraft Version: 1.6.1
    Operating System: Linux (amd64) version 3.5.0-36-generic
    Java Version: 1.7.0_25, Oracle Corporation
    Java VM Version: Java HotSpot&#8482; 64-Bit Server VM (mixed mode), Oracle Corporation
    Memory: 8246376 bytes (7 MB) / 55443456 bytes (52 MB) up to 954466304 bytes (910 MB)
    JVM Flags: 1 total; -Xmx1G
    AABB Pool Size: 0 (0 bytes; 0 MB) allocated, 0 (0 bytes; 0 MB) used
    Suspicious classes: No suspicious classes found.
    IntCache: cache: 0, tcache: 0, allocated: 0, tallocated: 0
    Launched Version: 1.6.1
    LWJGL: 2.9.0
    OpenGL: Gallium 0.4 on AMD PALM GL version 1.4 (2.1 Mesa 9.0.3), X.Org
    Is Modded: Probably not. Jar signature remains and client brand is untouched.
    Type: Client (map_client.txt)
    Resource Pack: Default
    Profiler Position: N/A (disabled)
    Vec3 Pool Size: ~~ERROR~~ NullPointerException: null[/COLOR]


I am using a Levono N585,
Prosser: AMD Comal
Ram: DDR3 1600 (AMD Comal)
Graphix Card: AMD Robson-XT

What should I do? What can I do? I have played minecraft with Linux Mint, and Windows [COLOR=#008000]*PUKE*[/COLOR] 8.

---

### Post by Cheesehead on 2013-07-06
Well, Minecraft works fine for me using the ordinary Java in the Ubuntu repositories. No need for a PPA.

---

### Post by TenPlus1 on 2013-07-07
Minrcraft was so annoying during setup and seemed slow on my system using java that I scrapped it altogether and went with MineTest which is a clone of MineCraft written in c++, is a lot smaller and very easy to install...  [http://minetest.net/](http://minetest.net/)

---

### Post by efflandt on 2013-07-07
Looks like a video issue. Not sure why minecraft recommends Oracle Java, it works fine with openjdk-6-jre or 7. I have heard that minecraft does not work well with Oracle Java 7, but cannot confirm that.

What does the following say about your video card and drivers it is using: sudo lspci -v

---

### Post by mark2741 on 2013-07-07
I had lots of trouble on 12.10 with Minecraft because I did it the hard way - I insisted on following Minecraft's instructions and using Oracle's JRE. Big mistake.

Make it easy on your self and start from scratch - uninstall the jre you have installed now, then just open up the Ubuntu Software Center and search for "Java" and then you'll see OpenJDK 7. Install that and then right-click on the minecraft.jar and do an Open With... and select the OpenJDK 7. Works perfectly.

---

### Post by oldrocker99 on 2013-07-07
Minetest is in the Ubuntu repos, and can be installed from the Software Center, or Synaptic, or simply:

sudo apt-get install minetest

Try it. You just might like it.

---

### Post by Iluvalar on 2013-07-09
The lwjgl bug is not too hard to fix. Download the latest lwjgl ([http://www.lwjgl.org/](http://www.lwjgl.org/)). After the initial download from the minecraft launcher, overwrite the appropriate files in /minecraft/bin and /minecraft/bin/natives

The game should run smoothly until the next update (where those files get overwrote by the wrong again, so you need to repeat every now and then).

Hope it help.

---

### Post by DarkAmbient on 2013-07-10
As long as you stick to the stable (1.5.2) version of Minecraft you could try Minecraftier which is found in my sig.

---

### Post by Horbo on 2013-07-10
Another fix for the lwjgl problem is to use Oracle Java 6 instead of 7.

---

### Post by SmartGoober on 2013-07-10
sudo lspci -v

00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
    Subsystem: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
    Flags: bus master, 66MHz, medium devsel, latency 32

00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 9809 (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device 397f
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 3000 [size=256]
    Memory at f0300000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx_updates, radeon

00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310]
    Subsystem: Lenovo Device 397f
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f0344000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:10.0 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03) (prog-if 30 [XHCI])
    Subsystem: Lenovo Device 397f
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at f0348000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [50] Power Management version 3
    Capabilities: [70] MSI: Enable- Count=1/8 Maskable- 64bit+
    Capabilities: [90] MSI-X: Enable+ Count=8 Masked-
    Capabilities: [a0] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Latency Tolerance Reporting
    Kernel driver in use: xhci_hcd

00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
    Subsystem: Lenovo Device 397f
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 43
    I/O ports at 3118 [size=8]
    I/O ports at 3124 [size=4]
    I/O ports at 3110 [size=8]
    I/O ports at 3120 [size=4]
    I/O ports at 3100 [size=16]
    Memory at f034e000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [50] MSI: Enable+ Count=1/8 Maskable- 64bit+
    Capabilities: [70] SATA HBA v1.0
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11) (prog-if 10 [OHCI])
    Subsystem: Lenovo Device 397f
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at f034d000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11) (prog-if 20 [EHCI])
    Subsystem: Lenovo Device 397f
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at f034c000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:13.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11) (prog-if 10 [OHCI])
    Subsystem: Lenovo Device 397f
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at f034b000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11) (prog-if 20 [EHCI])
    Subsystem: Lenovo Device 397f
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at f034a000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 14)
    Subsystem: Lenovo Device 397f
    Flags: 66MHz, medium devsel
    Kernel modules: i2c-piix4

00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
    Subsystem: Lenovo Device 397f
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at f0340000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
    Subsystem: Lenovo Device 397f
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64

00:15.0 PCI bridge: Advanced Micro Devices [AMD] Device 43a0 (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=05, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f0200000-f02fffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f00fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot-), MSI 00
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [b0] Subsystem: Advanced Micro Devices [AMD] Device 0000
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:15.1 PCI bridge: Advanced Micro Devices [AMD] Device 43a1 (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    Memory behind bridge: f0100000-f01fffff
    Prefetchable memory behind bridge: 00000000f0400000-00000000f04fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot-), MSI 00
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [b0] Subsystem: Advanced Micro Devices [AMD] Device 0000
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
    Flags: fast devsel

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
    Flags: fast devsel
    Capabilities: [f0] Secure device <?>
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
    Flags: fast devsel

00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
    Flags: fast devsel

00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
    Flags: fast devsel

00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
    Flags: fast devsel

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 07)
    Subsystem: Lenovo Device 397f
    Flags: bus master, fast devsel, latency 0, IRQ 44
    I/O ports at 2000 [size=256]
    Memory at f0004000 (64-bit, prefetchable) [size=4K]
    Memory at f0000000 (64-bit, prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
    Capabilities: [d0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 0d-00-00-00-68-4c-e0-00
    Kernel driver in use: r8169
    Kernel modules: r8169

06:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
    Subsystem: Lenovo Device 3118
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f0100000 (64-bit, non-prefetchable) [size=512K]
    Expansion ROM at f0400000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 2
    Capabilities: [50] MSI: Enable- Count=1/4 Maskable+ 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel driver in use: ath9k
    Kernel modules: ath9k

---

### Post by SmartGoober on 2013-07-10
Thank you guys, I am still trying to figure this out. I can't rember how I got this to work in Linux Mint. I paid $25 dollars, I want to use the real minecraft.

---

### Post by SmartGoober on 2013-07-10
> **Horbo said:**
> Another fix for the lwjgl problem is to use Oracle Java 6 instead of 7.

That fixed the problem, THANKS!

---

### Post by LordFran on 2013-07-12
When I do it, I use Suns JVM, and it works perfectly

---

