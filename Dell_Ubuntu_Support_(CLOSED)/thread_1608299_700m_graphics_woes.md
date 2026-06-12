---
title: "700m graphics woes"
date: 2010-10-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dpeley on 2010-10-28
I was wondering if there's any known problems or ways to get the graphics on the 700m to work better on moving pictures? (i'm talking internet videos/games/flash, haven't tested physical videos yet) i believe it's an 855gm intel card (not sure). The video always lags, or runs very haltingly, then if i try to full screen any kind of moving picture it slows way down.

currently it's set up to dual boot with about 10 gigs for xp just so i can do my videos and such still, but i'd like to cut all ties if possible.

Thanks guys!

---

### Post by darkhelmetchris on 2010-10-28
Could you please paste the output of
```
lspci
```
so I can see what graphics chipset you have

---

### Post by dpeley on 2010-10-29
sorry for the delay, here's the results:


00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:01.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)
02:04.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
02:04.1 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
02:04.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
02:04.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
02:05.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

---

### Post by darkhelmetchris on 2010-10-29
Okay, that's good information.  So we have this:
> **dpeley said:**
> 00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

And now we need just a little bit more info on that.  Run this command:
```
lspci -vv
```That will give us more detailed information.  Please paste the contents of the section that matches the quote above for your video adapter only (we don't need all the sections).

(for example, mine looks like this)
> 01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
    Subsystem: Giga-byte Technology Device d000
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 27
    Region 0: Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Region 1: I/O ports at ee00 [size=256]
    Region 2: Memory at fdfe0000 (32-bit, non-prefetchable) [size=64K]
    Region 5: Memory at fde00000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon


Once we have that section for yours, then we can implement some tweaks.

---

### Post by dpeley on 2010-11-01
Ok, here's the result once more:

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
    Subsystem: Dell Inspiron 700m/710m
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Region 0: Memory at <unassigned> (32-bit, prefetchable)
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
    Subsystem: Dell Inspiron 700m/710m
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
    Subsystem: Dell Inspiron 700m/710m
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) (prog-if 00 [VGA controller])
    Subsystem: Dell Inspiron 700m/710m
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at e8000000 (32-bit, prefetchable) [size=128M]
    Region 1: Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
    Region 2: I/O ports at 1800 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
    Subsystem: Dell Inspiron 700m/710m
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Region 0: Memory at f0000000 (32-bit, prefetchable) [size=128M]
    Region 1: Memory at e0080000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

---

### Post by darkhelmetchris on 2010-11-01
> **dpeley said:**
> 00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) (prog-if 00 [VGA controller])
..
Region 0: Memory at e8000000 (32-bit, prefetchable) [size=128M]
    Region 1: Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
    

Great.  This tells us that you have 128M of video memory with 512K reserved.

Credit where credit is due - the solution I'm about to share here comes from another forum at ubuntugeek.com.

Edit your xorg.conf with:
```
sudo gedit /etc/X11/xorg.conf
```Look for the "Device" section .. (yours may not be identical, but close.)
```
Section &#8220;Device&#8221;
          Identifier &#8220;Configured Video Device&#8221;
          Driver &#8220;intel&#8221;
EndSection
```After the "Driver" line, add these lines:
```
Section &#8220;Device&#8221;
          Identifier &#8220;Configured Video Device&#8221;
          Driver &#8220;intel&#8221;
          Option &#8220;AccelMethod&#8221; &#8220;UXA&#8221;
          VideoRam 130560
EndSection
```Note that 128M - 512K is 131072-512 = 130560

If you are using Compiz also, make this change to your Compiz settings using the Compiz Settings Manager:
- General options -> General -> remove the flag on Unredirect Fullscreen Windows
 - General options -> Display Settings -> remove the flag Sync To VBlank

... and then reboot your system

The chaps at ubuntugeek claim that the UXA acceleration is not on by default in Ubuntu 9.04, and so it's possible it might not be in 10.10 - your mileage may vary.

Let me know if this works for you.

---

### Post by dpeley on 2010-11-01
Unfortunately, no it didn't. the first command brought up the editor just fine, but the document (xorg.conf) was blank, nothing to edit. Is this normal?

---

### Post by squall1156 on 2010-11-02
Hey there.

Yes, it is normal for xorg.conf to be blank on a fresh 10.10 install.  I have a 700m also, and I'm seeing reasonable performance in windowed HD mode on YouTube, etc. after following the instructions for the Intel 855GM chipset that our laptops use.

Check out the following wiki entry - there are pretty clear instructions for manually enabling the correct driver AND applying a fix to the kernel to prevent instability as a result:

[[COLOR="DarkRed"]https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus[/COLOR]]("https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus")

Unfortunately, this driver still doesn't fix desktop effects.  Please let us know if your video performance is improved though.

---

### Post by dpeley on 2010-11-02
Thanks to both of you! this solved my problems perfectly so far. Everything works good now. You guys are very helpful.

---

