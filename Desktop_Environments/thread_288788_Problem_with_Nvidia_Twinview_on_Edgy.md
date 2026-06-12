---
title: "Problem with Nvidia Twinview on Edgy"
date: 2006-10-30
forum: Desktop Environments
---

### Post by digimatic on 2006-10-30
Hi.

I am having a strange problem with Twinview using the nvidia drivers after I upgraded to the Edgy release on my X86-64 system.

My video card is a quadro FX 500 which worked perfectly with twinview on Dapper, I have two analogue screens one of which is connected via a DVI-VGA converter.

I am using the same configuration as before on Dapper but as soon as I rebooted into Edgy I lost my 2nd screen. The odd thing is that as far as the gnome pager is concerned the screen is there, for example some windows open on the 2nd screen and by guessing the mouse position using the gnome pager I can drag them back to the working screen. Also the xorg logs seem to show no problems with the 2nd screen as it is detected and the resolution set to incorporate both screens in my twinview configuraiton.

Below are the relevant portions of my xorg.log and my xorg.conf files.

Any ideas anyone...I have tried following various howtos to enable twinview with different configurations and it all yields the same results..no signal on the 2nd screen.

I have also tried falling back to the nvidia-legacy driver package with the same results

(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "ConnectedMonitor" "CRT, CRT"
(**) NVIDIA(0): Option "RenderAccel" "1"
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "TwinViewOrientation" "RightOf"
(**) NVIDIA(0): Option "SecondMonitorHorizSync" "30-65"
(**) NVIDIA(0): Option "SecondMonitorVertRefresh" "50-75"
(**) NVIDIA(0): Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768; 800x
600,800x600"
(**) NVIDIA(0): Option "NoPowerConnectorCheck"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): TwinView enabled
(**) NVIDIA(0): ConnectedMonitor string: "CRT, CRT"
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): Skipping Power Connector Check.
(II) NVIDIA(0): NVIDIA GPU Quadro FX 500/FX 600 at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.18.13
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on Quadro FX 500/FX 600 at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     HP L1702 (CRT-0)
(--) NVIDIA(0):     NEC LCD71VM (CRT-1)
(--) NVIDIA(0): HP L1702 (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): NEC LCD71VM (CRT-1): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Devices: CRT-0, CRT-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024,1280x1024"
(II) NVIDIA(0):     "1024x768,1024x768"
(II) NVIDIA(0):     "800x600,800x600"
(II) NVIDIA(0): Virtual screen size determined to be 2560 x 1024
(--) NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X config option
(WW) NVIDIA(0): UBB is incompatible with the Composite extension.  Disabling
(WW) NVIDIA(0):     UBB.

xorg.conf

Section "Module"
#       Load    "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
#       Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "RenderAccel"           "1"
        Option          "TwinView" "1"
        Option          "ConnectedMonitor" "CRT, CRT"
        Option          "NoPowerConnectorCheck"
        Option          "TwinViewOrientation" "RightOf"
        Option          "SecondMonitorHorizSync" "30-65"
        Option          "SecondMonitorVertRefresh" "50-75"
        Option          "NoTwinViewXineramaInfo"
        Option          "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768; 800
x600,800x600"
EndSection
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-65
        VertRefresh     50-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

---

### Post by digimatic on 2006-11-06
I just applied the kernel update that appeared over the last few days and my twinview magically started working again.

So it must have been a kernel/Nvidia driver package issue, strange that others weren't reporting it though, maybe it was specific to particular Nvidia chipsets or something.

---

