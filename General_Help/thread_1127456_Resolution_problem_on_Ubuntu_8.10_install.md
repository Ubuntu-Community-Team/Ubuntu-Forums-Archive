---
title: "Resolution problem on Ubuntu 8.10 install"
date: 2009-04-16
forum: General Help
---

### Post by ghostu on 2009-04-16
Hi, I just installed Ubuntu 8.10 on an old dell.  It has an ATI All in Wonder 8500 connected to my HannsG 28" monitor.  I made it a dual boot system and under XP I get the full 1920x1200 resolution, but under Ubuntu (Gnome) I'm getting only 1280x1024 (and it looks like it's at 0Hz?).  Any way to get the max resolution going?

I'm all new to Linux, so any help would be great, but really want to learn.

Thanks!

---

### Post by LowSky on 2009-04-16
go to system>admin> restricted drivers, enable the ATI proprietart drivers, reboot and use the ATI Catalyst to set your screen

---

### Post by ghostu on 2009-04-16
> **LowSky said:**
> go to system>admin> restricted drivers, enable the ATI proprietart drivers, reboot and use the ATI Catalyst to set your screen

I went to System -> Administrator -> Hardware Drivers (I did not see Restricted Drivers).

Once there it says no proprietary drivers are in use on this system.  So there's nothing to select.

---

### Post by CatKiller on 2009-04-16
Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
```Bear in mind that these are the values for **my** monitor. You'll need to put in the values for **your** monitor, otherwise you could well permanently damage your monitor.

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       30-95
        VertRefresh     50-160
EndSection

```

---

### Post by ghostu on 2009-04-16
I'm hoping this might help out since I read these are the settings you guys may need to see:

lspci
---------------------------
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)


lspci -vv
---------------------------------
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]
    Subsystem: ATI Technologies Inc Device 0f2a
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at e0000000 (32-bit, prefetchable) [size=256M]
    Region 1: I/O ports at ec00 [size=256]
    Region 2: Memory at ff8f0000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at ff800000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: radeonfb


xorg.conf
----------------------------------
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---

### Post by Daisuke_Aramaki on 2009-04-16
> **ghostu said:**
> I'm hoping this might help out since I read these are the settings you guys may need to see:

lspci
---------------------------
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)


lspci -vv
---------------------------------
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]
    Subsystem: ATI Technologies Inc Device 0f2a
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at e0000000 (32-bit, prefetchable) [size=256M]
    Region 1: I/O ports at ec00 [size=256]
    Region 2: Memory at ff8f0000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at ff800000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: radeonfb


xorg.conf
----------------------------------
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

vesa is a safe fallback driver and it would work perfectly fine when you have an oboard graphic card and no proprietary ones like nvidia or intel. Try searching for catalyst driver in synaptic.

---

### Post by ghostu on 2009-04-16
I downloaded the Catalyst control manager, installed, then tried to run it and got the error you see in the pic below.

I'm thinking my video card is too old (Radeon All in Wonder 8500).  Any guesses now on what to do?

---

### Post by ghostu on 2009-04-16
Ok, got it working.  Uninstalled the catalyst control center and pointed xorg.conf to the correct driver and resolution.  That seemed to do it!

---

