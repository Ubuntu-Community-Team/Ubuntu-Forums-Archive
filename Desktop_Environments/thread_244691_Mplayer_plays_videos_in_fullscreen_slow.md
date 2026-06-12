---
title: "Mplayer plays videos in fullscreen slow"
date: 2006-08-26
forum: Desktop Environments
---

### Post by jrincon87 on 2006-08-26
I just installed mplayer because Totem-xine doens't have enough support for windows video files. Mplayer plays just about every video file I've got but when it comes to fullscreen, it's a disaster. The speed goes really slow in fullscreen mode. It doesn't happen when the size is normal. I've tried with almost every video driver that's included in mplayer. I think it might be a problem of the fps configuration. Not really sure how should I set it up.
Thanks.
PS: I downloaded the mplayer from the dapper repositories.

---

### Post by croak77 on 2006-08-27
What video driver are you using for X? nvidia, ati, mesa, etc...? How much memory do you have?

---

### Post by peabody on 2006-08-27
I can pretty much gaurantee this is because you don't have xv enabled.  Getting this up and running however depends on your video drivers.  What are you running?

---

### Post by jrincon87 on 2006-08-30
I'm using the video card that's integrated in the Board. I have 512MB RAM and an AMD Athlon 3.4ghz. I tried using all of the drivers in Mplayer. The only one I couldn't use was the xv. When I try to play something it displays an error saying something like: "error opening/initializing the selected video_out (-vo) device".
How can I fix this?

---

### Post by peabody on 2006-09-02
mmm, "on the board" is not enough information.  Could you try posting the output of sudo lspci -vvv

---

### Post by gkiller on 2006-09-02
Sorry to "hijack" this thread, but I have the same problem, and maybe someone can help me.

Many 720p videos (especially WMV) play slowly and out of sync here. I have a Radeon 9800 Pro (R350) graphics card and AthlonXP 2500+ CPU. This should just be enough to play the videos fine, because they do in Windows.

I use the fglrx driver that came with Dapper.
fglrxinfo shows:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.5814 (8.25.18)
```

Normally I use "mplayer -vo gl2", but "-vo x11" and others have the same problem. When I try "-vo xv", I get the following error:
```
It seems there is no Xvideo support for your video card available.
Run 'xvinfo' to verify its Xv support and read DOCS/HTML/en/video.html#xv!
See 'mplayer -vo help' for other (non-xv) video out drivers. Try -vo x11
Error opening/initializing the selected video_out (-vo) device.
```

Also when I go to the Gnome System->Preferences->Multimedia Systems Selector menu and choose "X Window System(X11/XShm/Xv)" as the default video output plugin, the test fails:
```
X Window System (X11/XShm/Xv): Resource busy or not available.
```
Choosing "Autodetect" or "X Window System(No Xv)" works.

xvinfo gives the following:
```
X-Video Extension version 2.2
screen #0
 no adaptors present
```
and xdpyinfo:
```
name of display:    :0.0
version number:    11.0
vendor string:    The X.Org Foundation
vendor release number:    70000000
X.Org version: 7.0.0
maximum request size:  16777212 bytes
motion buffer size:  256
bitmap unit, bit order, padding:    32, LSBFirst, 32
image byte order:    LSBFirst
number of supported pixmap formats:    7
supported pixmap formats:
    depth 1, bits_per_pixel 1, scanline_pad 32
    depth 4, bits_per_pixel 8, scanline_pad 32
    depth 8, bits_per_pixel 8, scanline_pad 32
    depth 15, bits_per_pixel 16, scanline_pad 32
    depth 16, bits_per_pixel 16, scanline_pad 32
    depth 24, bits_per_pixel 32, scanline_pad 32
    depth 32, bits_per_pixel 32, scanline_pad 32
keycode range:    minimum 8, maximum 255
focus:  window 0x380001f, revert to Parent
number of extensions:    31
    ATIFGLEXTENSION
    ATIFGLRXDRI
    ATITVOUT
    BIG-REQUESTS
    DAMAGE
    DPMS
    Extended-Visual-Information
    GLX
    MIT-SCREEN-SAVER
    MIT-SHM
    MIT-SUNDRY-NONSTANDARD
    RANDR
    RENDER
    SECURITY
    SGI-GLX
    SHAPE
    SYNC
    TOG-CUP
    X-Resource
    XC-APPGROUP
    XC-MISC
    XFIXES
    XFree86-Bigfont
    XFree86-DGA
    XFree86-DRI
    XFree86-Misc
    XFree86-VidModeExtension
    XInputExtension
    XKEYBOARD
    XTEST
    XVideo
default screen number:    0
number of screens:    1

screen #0:
  dimensions:    1280x1024 pixels (363x272 millimeters)
  resolution:    90x96 dots per inch
  depths (7):    24, 1, 4, 8, 15, 16, 32
  root window id:    0x75
  depth of root window:    24 planes
  number of colormaps:    minimum 1, maximum 1
  default colormap:    0x20
  default number of colormap cells:    256
  preallocated pixels:    black 0, white 16777215
  options:    backing-store NO, save-unders NO
  largest cursor:    64x64
  current input event mask:    0xfa6033
    KeyPressMask             KeyReleaseMask           EnterWindowMask
    LeaveWindowMask          ButtonMotionMask         KeymapStateMask
    StructureNotifyMask      SubstructureNotifyMask   SubstructureRedirectMask
    FocusChangeMask          PropertyChangeMask       ColormapChangeMask
  number of visuals:    64
  default visual id:  0x23
  visual:
    visual id:    0x23
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits

[...]
```


Any help is appreciated.

---

### Post by jrincon87 on 2006-09-02
The output is the following:
```
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 741/741GX/M741 Host (rev 03)
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 32
        Region 0: Memory at d0000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: [c0] AGP version 3.5
                Status: RQ=32 Iso- ArqSz=2 Cal=3 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3+ Rate=x4,x8
                Command: RQ=1 ArqSz=0 Cal=0 SBA+ AGP- GART64- 64bit- FW+ Rate=x8
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: cfe00000-cfefffff
        Prefetchable memory behind bridge: bfd00000-cfcfffff
        BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-

0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

0000:00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 0
        Region 4: I/O ports at 0c00 [size=32]

0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (prog-if 80 [Master])
        Subsystem: Silicon Integrated Systems [SiS] SiS5513 EIDE Controller (A,B step)
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 128
        Region 4: I/O ports at ffa0 [size=16]

0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0) (prog-if 00 [Generic])
        Subsystem: Elitegroup Computer Systems: Unknown device 0c04
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin C routed to IRQ 10
        Region 0: I/O ports at e800 [size=256]
        Region 1: I/O ports at ec00 [size=128]
        Capabilities: [48] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=55mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Silicon Integrated Systems [SiS] USB 1.0 Controller
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (20000ns max)
        Interrupt: pin A routed to IRQ 10
        Region 0: Memory at cfffd000 (32-bit, non-prefetchable) [size=4K]

0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Silicon Integrated Systems [SiS] USB 1.0 Controller
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (20000ns max)
        Interrupt: pin B routed to IRQ 3
        Region 0: Memory at cfffe000 (32-bit, non-prefetchable) [size=4K]

0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
        Subsystem: Silicon Integrated Systems [SiS] USB 2.0 Controller
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (20000ns max)
        Interrupt: pin D routed to IRQ 5
        Region 0: Memory at cffff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
        Subsystem: Silicon Integrated Systems [SiS] SiS900 10/100 Ethernet Adapter
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (13000ns min, 2750ns max)
        Interrupt: pin A routed to IRQ 11
        Region 0: I/O ports at e400 [size=256]
        Region 1: Memory at cfffc000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at cffc0000 [disabled] [size=128K]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:0b.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
        Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (500ns min, 6000ns max)
        Interrupt: pin A routed to IRQ 10
        Region 0: I/O ports at e000 [size=256]
        Capabilities: [c0] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter (prog-if 00 [VGA])
        Subsystem: Silicon Integrated Systems [SiS] [M]661xX/[M]741[GX]/[M]760 PCI/AGP VGA Adapter
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 11
        BIST result: 00
        Region 0: Memory at c0000000 (32-bit, prefetchable) [size=128M]
        Region 1: Memory at cfee0000 (32-bit, non-prefetchable) [size=128K]
        Region 2: I/O ports at dc00 [size=128]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [50] AGP version 3.0
                Status: RQ=256 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3+ Rate=x4,x8
                Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>

```
Thanks.

---

### Post by Anduu on 2006-09-03
To enable xv on Radeon find the section in your xorg.conf where fglrx is specified...it should have these options:

```
Section "Device"
	Identifier "aticonfig-Device[0]"
	Driver "fglrx"
	[COLOR="Red"]Option "VideoOverlay" "on"
	Option "OpenGLOverlay" "off"[/COLOR]
EndSection
```

As for SiS cards I have no clue :(

---

### Post by gkiller on 2006-09-05
Anduu:

Thanks for the answer. That worked, I can now use xv in mplayer.

But:

The playback may be a bit better, but it still loses sync pretty quickly, but now the audio keeps lagging behind (with gl2 the video lagged behind) and the videos become unwatchable. Also, compared to the x11 or gl2 video output, the video quality is really bad. I see aliasing artifacts (jagged egdes or fine structures that are flickering). It looks somehow like the movie is rendered in a really low resolution, then just resized to the actual size. This is even when I watch it in the original size, or half the size (then it's even worse).

Any idea why these issues might be and if there can be done anything to improve them? Or should I give up hope of watching high-resolution WMVs on Linux? :(

---

### Post by Anduu on 2006-09-05
Under the video tab in Mplayer preferences check "enable frame dropping"...it should help to keep things in sync.

BTW i have noticed on certain wmv's I get pretty bad performance as well...I blame microsoft for this not my pc ;)

---

### Post by gkiller on 2006-09-05
> **Anduu said:**
> Under the video tab in Mplayer preferences check "enable frame dropping"...it should help to keep things in sync.
Ok, that helped a bit. Now the audio lag is about constant 500-800 ms over a 3-minute video (except in the beginning)... but still not the same as in Windows :)

> BTW i have noticed on certain wmv's I get pretty bad performance as well...I blame microsoft for this not my pc ;)
Hehe :)

BTW, do you have any idea about the horrible image quality? I can't even do a screenshot comparison, because when I try take a xv screenshot with Ubuntu's utiliy, the video window is black. And with gxine's own Snapshot function I get perfect quality in the snapshot, but not in the video... ](*,)
But think of it like comparing the same 3D-game in 1280x1024 resolution with antialiasing (gl2) and 800x600 without antialiasing (xv). This is with every video, independent of codec and player, as long as xv is used.

---

