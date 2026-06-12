---
title: "screen resolution"
date: 2005-07-13
forum: Desktop Environments
---

### Post by hydra on 2005-07-13
hi ive just installed ubuntu and its working great...but the problem is that i want to change the screen resolution so that i can see the complete windows and stuff...ive tried changing it in preferences -->screen resolution but in there there's only a 640*480 resolution and its the only one...its there a way to change this so that i can see the windows and programs better???


thnx

---

### Post by varunus on 2005-07-13
What video card are you using?

The general method is to open your /etc/X11/xorg.conf, scroll down to the Screen section, and in each Display section, add new modes.  For example:

```

        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection

```

The mode that is first will be the default, and all will be available in the gnome control panel.

Some video cards need special procedures; which card do you have?  (if this doesn't work for you)

---

### Post by hydra on 2005-07-13
indeed it shows me this as u told me:

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Monitor         "SDM-HS53"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "720x400" "640x480"

```

as u can see it has the default screen but it has the other displays too  so how to change this??

---

### Post by varunus on 2005-07-13
Ahh, you have an intel integrated video card.  This card can sometimes have problems with screen resolutions (though i'm using the same card and don't have any problems, i've seen others that do).

Can you post your /etc/X11/xorg.conf and your /var/log/Xorg.0.log here please?

---

### Post by hydra on 2005-07-13
yep, here 

**/etc/X11/xorg.conf** 

```

#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
        FontPath        "unix/:7100"                    # local font server
        # if the local font server has problems, we can fall back on these
        FontPath        "/usr/lib/X11/fonts/misc"
        FontPath        "/usr/lib/X11/fonts/cyrillic"
        FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/Type1"
        FontPath        "/usr/lib/X11/fonts/CID"
        FontPath        "/usr/lib/X11/fonts/100dpi"
        FontPath        "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "la"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "SDM-HS53"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Monitor         "SDM-HS53"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

**/var/log/Xorg.0.log**
```

     
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul 13 16:21:37 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "SDM-HS53"
(**) |   |-->Device "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Int$(**) 
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.2
        X.Org Video Driver: 0.7
        X.Org XInput driver : 0.4
        X.Org Server Extension : 0.2
        X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
        i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, 915GM
(II) Primary Device is: PCI 00:02:0
(--) Chipset 845G found
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) Loading sub module "vbe"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/X11R6/lib/modules/libvbe.a
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 0.1.0
        ABI class: X.Org Video Driver, version 0.7
(**) I810(0): Depth 24, (--) framebuffer bpp 32
(==) I810(0): RGB weight 888
(==) I810(0): Default visual is TrueColor
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 8000 kB
(II) I810(0): VESA VBE OEM: Brookdale-G Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Brookdale-G Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Integrated Graphics Chipset: Intel(R) 845G
(--) I810(0): Chipset: "845G"
(--) I810(0): Linear framebuffer at 0xF0000000
(--) I810(0): IO registers at addr 0xEF800000
(II) I810(0): 1 display pipe available.
(II) I810(0): detected 8060 kB stolen memory.
(II) I810(0): I830CheckAvailableMemory: 200700 kB available
(II) I810(0): detected 8060 kB stolen memory.
(II) I810(0): I830CheckAvailableMemory: 200700 kB available
(II) I810(0): Will attempt to tell the BIOS that there is 12288 kB VideoRAM
(WW) I810(0): Extended BIOS function 0x5f11 not supported.
(II) I810(0): Before: SWF1 is 0x00000108
(II) I810(0): After: SWF1 is 0x00000108
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 8000 kB
(II) I810(0): VESA VBE OEM: Brookdale-G Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Brookdale-G Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): BIOS now sees 8000 kB VideoRAM
(--) I810(0): Pre-allocated VideoRAM: 8060 kByte
(==) I810(0): VideoRAM: 32768 kByte
(==) I810(0): video overlay key set to 0x101fe
(**) I810(0): page flipping disabled
(==) I810(0): Using gamma correction (1.0, 1.0, 1.0)
(II) I810(0): BIOS Build: 2758
(==) I810(0): Device Presence: disabled.
(==) I810(0): Display Info: enabled.
(II) I810(0): Broken BIOSes cause the system to hang here.
              If you encounter this problem please add
                 Option "DisplayInfo" "FALSE"
              to the Device section of your XF86Config file.
(II) I810(0): Display Info: CRT: attached: FALSE, present: FALSE, size: (0,0)

              to the Device section of your XF86Config file.
(II) I810(0): Display Info: CRT: attached: FALSE, present: FALSE, size: (0,0)(II) I810(0): Display Info: TV: attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: DFP (digital flat panel): attached: FALSE, prese$(II) I810(0): Display Info: LFP (local flat panel): attached: FALSE, present$(II) I810(0): Display Info: CRT2 (second CRT): attached: FALSE, present: FAL$(II) I810(0): Display Info: TV2 (second TV): attached: FALSE, present: FALSE$(II) I810(0): Currently active displays on Pipe A:
(II) I810(0):   CRT
(==) I810(0): Display is using Pipe A
(--) I810(0): Maximum frambuffer space: 32600 kByte
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level 2
(II) I810(0): VESA VBE DDC transfer in appr. 1 sec.
(II) I810(0): VESA VBE DDC read successfully
(II) I810(0): VESA VBE DDC transfer in appr. 1 sec.
(II) I810(0): VESA VBE DDC read successfully
(II) I810(0): Manufacturer: SNY  Model: 2250  Serial#: 16843009
(II) I810(0): Year: 2003  Week: 44
(II) I810(0): EDID Version: 1.3
(II) I810(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) I810(0): Sync:  Separate  Composite
(II) I810(0): Max H-Image Size [cm]: horiz.: 30  vert.: 23
(II) I810(0): Gamma: 2.20
(II) I810(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) I810(0): First detailed timing is preferred mode
(II) I810(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) I810(0): blueX: 0.149 blueY: 0.113   whiteX: 0.283 whiteY: 0.298
(II) I810(0): Supported VESA Video Modes:
(II) I810(0): 720x400@70Hz
(II) I810(0): 640x480@60Hz
(II) I810(0): 800x600@60Hz
(II) I810(0): 1024x768@60Hz
(II) I810(0): 800x600@60Hz
(II) I810(0): 1024x768@60Hz
(II) I810(0): Manufacturer's mask: 0
(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 65.0 MHz   Image Size:  304 x 228 mm
(II) I810(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344$(II) I810(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_b$(II) I810(0): Ranges: V min: 57  V max: 63 Hz, H min: 28  H max: 52 kHz, Pix$(II) I810(0): Monitor name: SDM-HS53
(II) I810(0): Using detected DDC timings
(II) I810(0):   HorizSync 28-52
(II) I810(0):   VertRefresh 57-63
(II) I810(0): Will use BIOS call 0x5f05 to set refresh rates for CRTs.
(--) I810(0): Maximum space available for video modes: 8000 kByte
Mode: 20 (132x25)
        ModeAttributes: 0xf
        WinAAttributes: 0x7
        ModeAttributes: 0xf
        WinAAttributes: 0x7
        WinBAttributes: 0x0
	WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc0005b77
        BytesPerScanline: 3200
        XResolution: 800
        YResolution: 600
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 32
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 3
        RedMaskSize: 8
        RedFieldPosition: 16
        GreenMaskSize: 8
        GreenFieldPosition: 8
        BlueMaskSize: 8
        BlueFieldPosition: 0
        RsvdMaskSize: 8
        RsvdFieldPosition: 24
        DirectColorModeInfo: 0
        PhysBasePtr: 0xf0000000
        LinBytesPerScanLine: 3200
        BnkNumberOfImagePages: 3
        LinNumberOfImagePages: 3
        LinRedMaskSize: 8
        LinRedFieldPosition: 16
        LinGreenMaskSize: 8
        LinGreenFieldPosition: 8
        LinBlueMaskSize: 8
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 8
        LinRsvdFieldPosition: 24
        MaxPixelClock: 230000000
*Mode: 54 (1024x768)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc0005b77
        BytesPerScanline: 4096
        XResolution: 1024
        YResolution: 768
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 32
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 1
        RedMaskSize: 8
        RedFieldPosition: 16
        GreenMaskSize: 8
        GreenFieldPosition: 8
        BlueMaskSize: 8
        BlueFieldPosition: 0
        RsvdMaskSize: 8
        RsvdFieldPosition: 24
        DirectColorModeInfo: 0
        PhysBasePtr: 0xf0000000
        LinBytesPerScanLine: 4096
        BnkNumberOfImagePages: 1
        LinNumberOfImagePages: 1
        LinRedMaskSize: 8
        LinRedFieldPosition: 16
        LinGreenMaskSize: 8
        LinGreenFieldPosition: 8
        LinBlueMaskSize: 8
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 8
        LinRsvdFieldPosition: 24
        MaxPixelClock: 230000000
*(WW) (1280x1024,SDM-HS53) mode clock 132.751MHz exceeds DDC maximum 90MHz
(WW) (1280x1024,SDM-HS53) mode clock 132.751MHz exceeds DDC maximum 90MHz
(WW) (1280x1024,SDM-HS53) mode clock 132.751MHz exceeds DDC maximum 90MHz
(WW) (1280x1024,SDM-HS53) mode clock 128.943MHz exceeds DDC maximum 90MHz
(WW) (1280x1024,SDM-HS53) mode clock 128.943MHz exceeds DDC maximum 90MHz
(WW) (1280x1024,SDM-HS53) mode clock 108.78MHz exceeds DDC maximum 90MHz
(WW) (1280x1024,SDM-HS53) mode clock 108.78MHz exceeds DDC maximum 90MHz
(WW) (1280x1024,SDM-HS53) mode clock 108.78MHz exceeds DDC maximum 90MHz
(WW) (1280x1024,SDM-HS53) mode clock 108.78MHz exceeds DDC maximum 90MHz
(WW) (1280x1024,SDM-HS53) mode clock 108.78MHz exceeds DDC maximum 90MHz
(WW) (1280x1024,SDM-HS53) mode clock 108.78MHz exceeds DDC maximum 90MHz
(WW) (1280x1024,SDM-HS53) mode clock 108.78MHz exceeds DDC maximum 90MHz
(WW) (1280x1024,SDM-HS53) mode clock 108.78MHz exceeds DDC maximum 90MHz
(WW) (1280x1024,SDM-HS53) mode clock 108.78MHz exceeds DDC maximum 90MHz
(WW) (1280x1024,SDM-HS53) mode clock 108.78MHz exceeds DDC maximum 90MHz
(WW) (1280x1024,SDM-HS53) mode clock 100.389MHz exceeds DDC maximum 90MHz
(WW) (1280x1024,SDM-HS53) mode clock 100.389MHz exceeds DDC maximum 90MHz
(WW) (1280x1024,SDM-HS53) mode clock 100.389MHz exceeds DDC maximum 90MHz
(WW) (1280x1024,SDM-HS53) mode clock 100.389MHz exceeds DDC maximum 90MHz
Mode: 58 (1280x1024)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc0005b77
        BytesPerScanline: 5120
        XResolution: 1280
        YResolution: 1024
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 32
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 8
        RedFieldPosition: 16
        GreenMaskSize: 8
        GreenFieldPosition: 8
        BlueMaskSize: 8
        BlueFieldPosition: 0
        RsvdMaskSize: 8
        RsvdFieldPosition: 24
        DirectColorModeInfo: 0
        PhysBasePtr: 0xf0000000
        LinBytesPerScanLine: 5120
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 8
        LinRedFieldPosition: 16
        LinGreenMaskSize: 8
        LinGreenFieldPosition: 8
        LinBlueMaskSize: 8
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 8
        LinRsvdFieldPosition: 24
        MaxPixelClock: 230000000
*(WW) (1600x1200,SDM-HS53) mode clock 195.84MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,SDM-HS53) mode clock 195.84MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,SDM-HS53) mode clock 195.84MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,SDM-HS53) mode clock 190.247MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,SDM-HS53) mode clock 190.247MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,SDM-HS53) mode clock 160.833MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,SDM-HS53) mode clock 160.833MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,SDM-HS53) mode clock 160.833MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,SDM-HS53) mode clock 160.833MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,SDM-HS53) mode clock 160.833MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,SDM-HS53) mode clock 160.833MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,SDM-HS53) mode clock 160.833MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,SDM-HS53) mode clock 160.833MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,SDM-HS53) mode clock 160.833MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,SDM-HS53) mode clock 160.833MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,SDM-HS53) mode clock 148.759MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,SDM-HS53) mode clock 148.759MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,SDM-HS53) mode clock 148.759MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,SDM-HS53) mode clock 148.759MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,SDM-HS53) mode clock 111.703MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,SDM-HS53) mode clock 111.703MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,SDM-HS53) mode clock 111.703MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,SDM-HS53) mode clock 111.703MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,SDM-HS53) mode clock 111.703MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,SDM-HS53) mode clock 111.703MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,SDM-HS53) mode clock 111.703MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,SDM-HS53) mode clock 111.703MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,SDM-HS53) mode clock 111.703MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,SDM-HS53) mode clock 111.703MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,SDM-HS53) mode clock 111.703MHz exceeds DDC maximum 90MHz
Mode: 5a (1600x1200)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc0005b77
        BytesPerScanline: 6400
        XResolution: 1600
        YResolution: 1200
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 32
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 8
        RedFieldPosition: 16
        GreenMaskSize: 8
        GreenFieldPosition: 8
        BlueMaskSize: 8
        BlueFieldPosition: 0
        RsvdMaskSize: 8
        RsvdFieldPosition: 24
        DirectColorModeInfo: 0
        PhysBasePtr: 0xf0000000
        LinBytesPerScanLine: 6400
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 8
        LinRedFieldPosition: 16
        LinGreenMaskSize: 8
        LinGreenFieldPosition: 8
        LinBlueMaskSize: 8
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 8
        LinRsvdFieldPosition: 24
        MaxPixelClock: 230000000
Mode: 5c (1920x1440)
        ModeAttributes: 0x9a
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc0005b77
        BytesPerScanline: 7680
        XResolution: 1920
        YResolution: 1440
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 32
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 8
        RedFieldPosition: 16
        GreenMaskSize: 8
        GreenFieldPosition: 8
        BlueMaskSize: 8
        BlueFieldPosition: 0
        RsvdMaskSize: 8
        RsvdFieldPosition: 24
        DirectColorModeInfo: 0
        PhysBasePtr: 0xf0000000
        LinBytesPerScanLine: 7680
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 8
        LinRedFieldPosition: 16
        LinGreenMaskSize: 8
        LinGreenFieldPosition: 8
        LinBlueMaskSize: 8
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 8
        LinRsvdFieldPosition: 24
        MaxPixelClock: 230000000
(II) I810(0): SDM-HS53: Using default hsync range of 28.00-52.00 kHz
(II) I810(0): SDM-HS53: Using default vrefresh range of 57.00-63.00 Hz
(II) I810(0): Not using mode "1024x768" (no mode of this name)
(II) I810(0): Not using mode "800x600" (no mode of this name)
(II) I810(0): Not using mode "720x400" (no mode of this name)
(1024x768,SDM-HS53) mode clock 100000MHz exceeds DDC maximum 90MHz
(800x600,SDM-HS53) mode clock 100000MHz exceeds DDC maximum 90MHz
(720x400,SDM-HS53) mode clock 100000MHz exceeds DDC maximum 90MHz
(II) I810(0): Increasing the scanline pitch to allow tiling mode (640 -> 1024).
(--) I810(0): Virtual size is 640x480 (pitch 1024)
(**) I810(0): *Built-in mode "640x480"
(II) I810(0): Attempting to use 60Hz refresh for mode "640x480" (50)
(--) I810(0): Display dimensions: (300, 230) mm
(--) I810(0): DPI set to (54, 53)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.2.0
        ABI class: X.Org Video Driver, version 0.7
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 0.1.0
        ABI class: X.Org Video Driver, version 0.7
(==) I810(0): VBE Restore workaround: enabled.
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/X11R6/lib/modules/libshadow.a
(II) Module shadow: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.2
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) I810(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Indirect CPU to Screen color expansion
        Solid Horizontal and Vertical Lines
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                21 128x128 slots
                5 256x256 slots
(==) I810(0): Backing store disabled
(==) I810(0): Silken mouse enabled
(II) I810(0): Initializing HW Cursor
(**) Option "dpms"
(**) I810(0): DPMS enabled
(II) I810(0): X context handle = 0x00000001
(II) I810(0): [drm] installed DRM signal handler
(II) I810(0): [DRI] installation complete
(II) I810(0): direct rendering: Enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "la"
(**) Generic Keyboard: XkbLayout: "la"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Could not init font path element unix/:7100, removing from list!

```

this last is pretty long n i supposed the only part u care about is the one setting the displays so i couldnt paste it all

---

### Post by varunus on 2005-07-13
I did a little reading on this, and I think I may have found a possible solution:

Go into your BIOS and check to see how much RAM has been given to the intel.  Make sure it is at least 8 MB.  If it is, or if there is no listing in your BIOS for how much RAM your card has (or if setting it in BIOS just doesn't work) try the following:

Change your device section in your xorg.conf to read:

Section "Device"
        Identifier      "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Driver          "i810"
        VideoRam        65536
        BusID           "PCI:0:2:0"
EndSection

Where the number after video ram is the number of Kilobytes of RAM your card has.  Make sure, once again, that you set it to at least 8192.  Can you go above 640x480 now?  If not, there's another thing we can try...

---

### Post by hydra on 2005-07-13
with which command can i get that info?? ive tried

dmesg but it doesnt show anything interesting

---

### Post by hydra on 2005-07-13
ok so ive changed the info so that it shows me:

Section "Device"
Identifier "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
Driver "i810"
VideoRam 8192
BusID "PCI:0:2:0"
EndSection

but i still cant get any other resolution

---

### Post by maruchan on 2005-07-13
hydra, you might want to expand that monitor section so the system knows what frequencies work. I found the xorg.conf of someone with your monitor; here's what they had:

> Section "Monitor"
Identifier "SDM-HS53"
HorizSync 28 - 48
VertRefresh 57 - 63
Option "DPMS"
EndSection

This is considerably more than what you have in your conf file, so I'd try it out.

---

### Post by jvandub on 2005-07-14
I'm sorry I just installed Ubuntu today and I've never used linux before.  Could you explain how to do this to someone who is pretty much new to all of this.  I'm good with Windows but I just have no idea with linux.  I'm having the same resolution problem and I have Intel Integrated as well.

---

### Post by maruchan on 2005-07-14
jvandub, post all your system specs or PM me. Depending on how you feel about hijacking threads.

---

### Post by hydra on 2005-07-14
thnx ive tried that thing of changing the sttings but still i get the same resolution :|

---

### Post by varunus on 2005-07-14
Hydra,

I found a howto that might help you; it worked for someone I know.  Try this: [http://ubuntuforums.org/showthread.php?t=27029](http://ubuntuforums.org/showthread.php?t=27029)

This will use the 855 resolution program to add new resolutions (seems some buggy BIOSes don't like the i810 driver for linux.

Good luck.

Varunus

---

### Post by spednik on 2005-07-14
I Had this exact problem on A Dell Inspiron 1100 Laptop, it had an Intel integrated card. as someone mentioned before, the problem with this machine (dont know if its similar to yours) is that the BIOS doesnt allocate enough ram to the X server. I got this fix from the ubuntu wiki, it worked for me. 


```
    *

      . The Inspiron 1100 comes with a 1024x768 screen by default, but it will set your screen to 800x600 and won't give you the option to change it under screen resolution. To fix this once everything has installed, boot to the Root Terminal or use Applications>System Tools>Root Terminal. Once logged in, type (without quotes) "sudo nano /etc/X11/xorg.conf". From nano, go down to where it says "Section "Monitor"". Delete everything after that and replace it with the following (which was generated by Red Hat Fedora Core):

Section "Monitor"
        Identifier      "Generic Monitor"
        ModelName       "Dell 1024x768 Laptop Display Panel"
        HorizSync       31.5 - 48.5
        VertRefresh     59.0 - 75.0
        Option          "DPMS"
EndSection

Section "Device"
        Identifier      "Videocard0"
        Driver          "i810"
        VendorName      "Videocard vendor"
        BoardName       "Intel 845"
        VideoRam                        10000
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubsection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection
```

---

### Post by hydra on 2005-07-14
YEAHHH :razz:  thnx u guys all of u....i got this fixed adding resolutions to the ones that exists, installing 855 resolution (THNX varunus)  after adding the resolutions just restart it with CRT + ALT + back i think or just boot it,  here is my **xorg.conf**

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"la"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	VideoRam         8192
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"SDM-HS53"
	HorizSync        28 - 48
	VertRefresh      57 - 63
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"SDM-HS53"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		**"1280x1024" "1152x864"** "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		**"1280x1024" "1152x864"** "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		**"1280x1024" "1152x864"** "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		**"1280x1024" "1152x864"** "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		**"1280x1024" "1152x864"** "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		**"1280x1024" "1152x864"** "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

as u can see i put the resolutions i add in black, after being added i just boot and i got the login page in different resolution but it was very at the left so i just do this for my SONY 15" monitor to get it done perfectly I just push the button *Menu -->Screen --> Auto* and this should get the job done so now my desktop has a 1024*768, 800*600  and 640*480 resolutions available....  

thnx  really ;)

---

### Post by Akir on 2005-07-16
You're IGC is on the i815 motherboard chipset, correct? I'm having the same problems. The card should be giving much higher resolutions. This is really bugging me persionally, because I normally use a high resolution to fit my large CRT screen.

---

### Post by hydra on 2005-07-16
Different specs...but have u tried everything put in the xorg.conf :

[list]
1.VideoRam         8192

2.HorizSync        28 - 48
   VertRefresh      57 - 63  <-----this depends on ur monitor mines is "SDM-HS53"

3. Adding more resolutions **"1280x1024" "1152x864"** "1024x768" "800x600" "720x400" "640x480"
[/list]

have u tried all of it.....what monitor or intel device do u have??

---

### Post by Luggy on 2005-07-17
I was getting 1280x768 but I wanted 1280x1024.

```
        SubSection "Display"
                Depth           24
                Modes           "1280x1024"
        EndSubSection
``` 

This kept me stuck at 1280x1024

```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
**        HorizSync       28-72**
        VertRefresh     43-72
        EndSection
``` 

changing my HorizSync fixed that \\:D/

---

### Post by Irony on 2005-07-17
Don't change your monitor Vert and Horiz rates until you know what they are or you won't boot up in graphical mode.

I used the LiveCD to determine what the correct settings were, as the LiveCD was at the correct resolution. In other words boot up the LiveCD then when it all done go to desktop right click and open a terminal, type;

gedit /etc/X11/xorg.conf

Scroll down and look at the numbers in that file. Then boot up into the installed ubuntu and to change anything go;

sudo gedit /etc/X11/xorg.conf

Make the changes and save.

---

### Post by varunus on 2005-07-17
For those of you still having problems, use the 855resolution utility to correct your problem.  It works for computers for which changing the horizsync and vertrefresh fails (by getting around a problem with some buggy bioses).  Here's the link again: [http://ubuntuforums.org/showthread.php?t=27029](http://ubuntuforums.org/showthread.php?t=27029)

---

### Post by Luggy on 2005-07-17
[QUOTE=Irony]Don't change your monitor Vert and Horiz rates until you know what they are or you won't boot up in graphical mode.

I used the LiveCD to determine what the correct settings were, as the LiveCD was at the correct resolution. In other words boot up the LiveCD then when it all done go to desktop right click and open a terminal, type;

gedit /etc/X11/xorg.conf

Scroll down and look at the numbers in that file. Then boot up into the installed ubuntu and to change anything go;

sudo gedit /etc/X11/xorg.conf

Make the changes and save.[/QUOTE]

I that method might only work for some monitors though. Whenever I booted up the liveCD prior to the install it kept me at 1024x768.

---

### Post by Dukeman330 on 2005-07-17
[QUOTE=hydra]hi ive just installed ubuntu and its working great...but the problem is that i want to change the screen resolution so that i can see the complete windows and stuff...ive tried changing it in preferences -->screen resolution but in there there's only a 640*480 resolution and its the only one...its there a way to change this so that i can see the windows and programs better???


thnx[/QUOTE]
 So... after spending about a day playing around with configuration suggestions from other people, I finally tried following the autoconfiguration deal at the top of the xorg.conf file.  Specifically:

   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
   sudo dpkg-reconfigure xserver-xorg

This walks you though a whole host of interesting configuration options, but specifically lets you choose a default resolution.  I picked 800x600, and when I rebooted my computer, that's what I got.  Good luck.

---

