---
title: "Installing gnome display manager"
date: 2013-01-15
forum: Desktop Environments
---

### Post by Raafat1991 on 2013-01-15
Hi gusy...after i executed this :

```
sudo apt-get install mdm mint-mdm-themes 
```

display becomes bad ( applications,places in top-left-corner) i don't want that style i want gnome style (when my mouse over top-left-corner all applications and my windows pop up )...please guys the new style is bad....help me

---

### Post by Frogs Hair on 2013-01-15
What operating system ? Below is the description of the themes you installed.  > Themes for the MDM display manager

If you are using Ubuntu and want to install the Gnome Shell it is in the software center. You will want to install the Gnome Tweak Tool also.

After installation log out and in and select Gnome from the log-in list.

---

### Post by Raafat1991 on 2013-01-16
> **Frogs Hair said:**
> What operating system ? Below is the description of the themes you installed.  

If you are using Ubuntu and want to install the Gnome Shell it is in the software center. You will want to install the Gnome Tweak Tool also.

After installation log out and in and select Gnome from the log-in list.

My operating system is ubuntu 12.04 LTS

i did what you said but the same....

---

### Post by kansasnoob on 2013-01-16
Hmmmm, mdm is Mint's display manager I believe. What desktop environment are you running?

---

### Post by Raafat1991 on 2013-01-16
> **kansasnoob said:**
> Hmmmm, mdm is Mint's display manager I believe. What desktop environment are you running?

I don't know :D

---

### Post by ibjsb4 on 2013-01-16
> **Raafat1991 said:**
> I don't know :D

```
echo $DESKTOP_SESSION
```

---

### Post by Raafat1991 on 2013-01-16
> **ibjsb4 said:**
> ```
echo $DESKTOP_SESSION
```

ubuntu

---

### Post by Frogs Hair on 2013-01-17
From the icon on the right of the greeter box select Gnome during login.

---

### Post by Raafat1991 on 2013-01-19
> **Frogs Hair said:**
> From the icon on the right of the greeter box select Gnome during login.

Hi...i did what you said and i executed this command :

```
echo $DESKTOP_SESSION
```and this is its output :

```
gnome-shell
```
but the same....

---

### Post by Frogs Hair on 2013-01-19
The Gnome Shell should say activities in the top left corner with the default theme. If you are seeing the old style menu on the top panel you are logged into classic or it is defaulting to that desktop.

Normally if you can run Unity 3D (Ubuntu) you can run the shell but others have had a problem being able to log into the shell. If that is the case there are threads on the forum that speak to that problem so I would look for them first. 

Posting some information about your computer and graphics card may be helpful. The following will display information about your Graphics card/chip and driver.  ```
lspci -v 
```

---

### Post by Raafat1991 on 2013-01-20
> **Frogs Hair said:**
> The Gnome Shell should say activities in the top left corner with the default theme. If you are seeing the old style menu on the top panel you are logged into classic or it is defaulting to that desktop.

Normally if you can run Unity 3D (Ubuntu) you can run the shell but others have had a problem being able to log into the shell. If that is the case there are threads on the forum that speak to that problem so I would look for them first. 

Posting some information about your computer and graphics card may be helpful. The following will display information about your Graphics card/chip and driver.  ```
lspci -v 
```

Here what you want :

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device 1277
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: db000000-dc0fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000d1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 1682
    Flags: bus master, fast devsel, latency 0, IRQ 50
    Memory at dc400000 (64-bit, non-prefetchable) [size=4M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at e000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 1277
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at df00a000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei
    Kernel modules: mei

00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1277
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at df008000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 1ac3
    Flags: bus master, fast devsel, latency 0, IRQ 51
    Memory at df000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: de600000-deffffff
    Prefetchable memory behind bridge: 00000000d4200000-00000000d4bfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: ddc00000-de5fffff
    Prefetchable memory behind bridge: 00000000d3700000-00000000d40fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: dd200000-ddbfffff
    Prefetchable memory behind bridge: 00000000d2c00000-00000000d35fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: dc800000-dd1fffff
    Prefetchable memory behind bridge: 00000000d2100000-00000000d2afffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1277
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at df007000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 1277
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device 1277
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 41
    I/O ports at e0b0 [size=8]
    I/O ports at e0a0 [size=4]
    I/O ports at e090 [size=8]
    I/O ports at e080 [size=4]
    I/O ports at e060 [size=32]
    Memory at df006000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 1277
    Flags: medium devsel, IRQ 11
    Memory at df005000 (64-bit, non-prefetchable) [size=256]
    I/O ports at e040 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: NVIDIA Corporation GF119 [GeForce GT 520MX] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 1762
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at db000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at d000 [size=128]
    Expansion ROM at dc000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_experimental_304, nvidia_experimental_310, nouveau, nvidiafb

03:00.0 Network controller: Intel Corporation Centrino Wireless-N 100
    Subsystem: Intel Corporation Centrino Wireless-N 100 BGN
    Flags: bus master, fast devsel, latency 0, IRQ 49
    Memory at ddc00000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

04:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1059
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at dd200000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device 1277
    Flags: bus master, fast devsel, latency 0, IRQ 47
    I/O ports at 9000 [size=256]
    Memory at d2104000 (64-bit, prefetchable) [size=4K]
    Memory at d2100000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

```

---

### Post by Frogs Hair on 2013-01-20
You should have no problem running the shell with this Graphics card so I can only suggest searching because the problem has occurred before.  

```
1:00.0 VGA compatible controller: NVIDIA Corporation GF119 [GeForce GT 520MX] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 1762
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at db000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at d000 [size=128]
    Expansion ROM at dc000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_experimental_304, nvidia_experimental_310, nouveau, nvidiafb
```

---

### Post by Raafat1991 on 2013-01-22
> **Frogs Hair said:**
> You should have no problem running the shell with this Graphics card so I can only suggest searching because the problem has occurred before.  

```
1:00.0 VGA compatible controller: NVIDIA Corporation GF119 [GeForce GT 520MX] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 1762
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at db000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at d000 [size=128]
    Expansion ROM at dc000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_experimental_304, nvidia_experimental_310, nouveau, nvidiafb
```


Thank you....

---

### Post by Raafat1991 on 2013-01-22
Please guys i need your helllllllllllllllllllp this interface is bad bad bad i want gnome interface...

---

### Post by Frogs Hair on 2013-01-22
Try the following,restart and login to Gnome.  

```
sudo apt-get install --reinstall gnome-shell
```

---

### Post by Raafat1991 on 2013-01-23
> **Frogs Hair said:**
> Try the following,restart and login to Gnome.  

```
sudo apt-get install --reinstall gnome-shell
```

Also no luck....

---

### Post by Raafat1991 on 2013-01-25
Guys...please

---

### Post by Frogs Hair on 2013-01-25
I can't think of or see any reason it's not working but you can take a look at the link. [https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10)

---

### Post by Raafat1991 on 2013-01-27
> **Frogs Hair said:**
> I can't think of or see any reason it's not working but you can take a look at the link. [https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10)

Hi...this what i got :

```
E: Unable to locate package ubuntu-gnome-desktop
E: Unable to locate package ubuntu-gnome-default-settings

```after executing :

```

[LIST]
[*]**sudo apt-get install ubuntu-gnome-desktop ubuntu-gnome-default-settings**
[/LIST]

```

---

### Post by Frogs Hair on 2013-01-27
The link is for a version of 12.10 that comes with the Gnome Shell instead of Unity and would require a clean installation. It can't be installed via the command line. For what ever reason the Gnome Shell is not working on your current installation and it may be related to the attempt install the Mint window manager and themes mentioned in the first post.

---

### Post by Krytarik on 2013-01-27
You know, it would be interesting to know what exactly you are seeing at this point, as it definitely can't be anything else than Gnome Shell or a broken version of it:
> **Raafat1991 said:**
> Hi...i did what you said and i executed this command :

```
echo $DESKTOP_SESSION
```and this is its output :

```
gnome-shell
```but the same....

Also, your hybrid graphics setup might be the culprit of any graphical issues you might be experiencing:
> **Raafat1991 said:**
> ```
[...]

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core  Processor Family Integrated Graphics Controller (rev 09) (prog-if 00  [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 1682
    Flags: bus master, fast devsel, latency 0, IRQ 50
    Memory at dc400000 (64-bit, non-prefetchable) [size=4M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at e000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

[...]

01:00.0 VGA compatible controller: NVIDIA Corporation GF119 [GeForce GT 520MX] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 1762
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at db000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at d000 [size=128]
    Expansion ROM at dc000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_experimental_304, nvidia_experimental_310, nouveau, nvidiafb

[...]
```
Regards.

---

### Post by Raafat1991 on 2013-01-28
Guuuuuuuuuuuuuuys...that's disappointed  ](*,)

---

### Post by Raafat1991 on 2013-02-06
Is there a hope for my problem ?

---

