---
title: "Hidden top panel/bar."
date: 2015-04-18
forum: Desktop Environments
---

### Post by vettel3 on 2015-04-18
I think my gnome top bar has a different resolution then the rest of the components. This is how it looks like atm: 
[http://pl.tinypic.com/r/zx729h/8](http://pl.tinypic.com/r/zx729h/8)

Only after changing scale for menu and title bars in 'Displays' menu you can see (only a part of it) that top bar is hidden outside of the screen:
[http://pl.tinypic.com/r/2s8r32p/8](http://pl.tinypic.com/r/2s8r32p/8)

Do you have any ideas how to make top bar (this one with battery state, time, date etc.) visible?

---

### Post by deadflowr on 2015-04-18
Could you provide information on the graphics card and the monitor?

---

### Post by vettel3 on 2015-04-18
VGA compatible controller [0300]: NVIDIA Corporation GT218M [NVS 3100M] [10de:0a6c] (rev a2) Subsystem: Dell Device [1028:040a]

 product: GT218M [NVS 3100M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0





"Default Screen Section" for depth/fbbpp 24/32
[    21.000] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    21.000] (==) NVIDIA(0): RGB weight 888
[    21.000] (==) NVIDIA(0): Default visual is TrueColor
[    21.000] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    21.001] (**) NVIDIA(0): Enabling 2D acceleration
[    22.310] (WW) NVIDIA(GPU-0): Unable to read EDID for display device DFP-3
[    22.319] (II) NVIDIA(GPU-0): Display (Chi Mei Optoelectronics corp. (DFP-3)) does not
[    22.319] (II) NVIDIA(GPU-0):     support NVIDIA 3D Vision stereo.
[    22.322] (II) NVIDIA(0): NVIDIA GPU NVS 3100M (GT218) at PCI:1:0:0 (GPU-0)
[    22.322] (--) NVIDIA(0): Memory: 524288 kBytes
[    22.322] (--) NVIDIA(0): VideoBIOS: 70.18.53.00.04
[    22.322] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    22.322] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    22.338] (II) NVIDIA(GPU-0): Display (Chi Mei Optoelectronics corp. (DFP-3)) does not
[    22.338] (II) NVIDIA(GPU-0):     support NVIDIA 3D Vision stereo.
[    22.566] (--) NVIDIA(0): Valid display device(s) on NVS 3100M at PCI:1:0:0
[    22.566] (--) NVIDIA(0):     CRT-0
[    22.566] (--) NVIDIA(0):     DFP-0
[    22.566] (--) NVIDIA(0):     DFP-1
[    22.566] (--) NVIDIA(0):     DFP-2
[    22.566] (--) NVIDIA(0):     Chi Mei Optoelectronics corp. (DFP-3) (connected)
[    22.566] (--) NVIDIA(0):     DFP-4
[    22.566] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    22.566] (--) NVIDIA(0): DFP-0: 165.0 MHz maximum pixel clock
[    22.566] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    22.566] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
[    22.566] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    22.566] (--) NVIDIA(0): DFP-2: 480.0 MHz maximum pixel clock
[    22.566] (--) NVIDIA(0): DFP-2: Internal DisplayPort
[    22.566] (--) NVIDIA(0): Chi Mei Optoelectronics corp. (DFP-3): 480.0 MHz maximum pixel clock
[    22.566] (--) NVIDIA(0): Chi Mei Optoelectronics corp. (DFP-3): Internal DisplayPort
[    22.566] (--) NVIDIA(0): DFP-4: 480.0 MHz maximum pixel clock
[    22.566] (--) NVIDIA(0): DFP-4: Internal DisplayPort
[    22.566] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    22.566] (**) NVIDIA(0):     device Chi Mei Optoelectronics corp. (DFP-3) (Using EDID
[    22.566] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[    22.573] (==) NVIDIA(0): 
[    22.573] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    22.573] (==) NVIDIA(0):     will be used as the requested mode.
[    22.573] (==) NVIDIA(0): 
[    22.573] (II) NVIDIA(0): Validated MetaModes:
[    22.573] (II) NVIDIA(0):     "DFP-3:nvidia-auto-select"
[    22.573] (II) NVIDIA(0): Virtual screen size determined to be 1280 x 800
[    22.599] (--) NVIDIA(0): DPI set to (108, 106); computed from "UseEdidDpi" X config
[    22.599] (--) NVIDIA(0):     option
[    22.599] (II) UnloadModule: "nouveau"
[    22.599] (II) Unloading nouveau
[    22.599] (II) UnloadModule: "modesetting"
[    22.599] (II) Unloading modesetting
[    22.599] (II) UnloadModule: "fbdev"
[    22.599] (II) Unloading fbdev
[    22.599] (II) UnloadSubModule: "fbdevhw"
[    22.599] (II) Unloading fbdevhw
[    22.599] (II) UnloadModule: "vesa"
[    22.599] (II) Unloading vesa
[    22.599] (--) Depth 24 pixmap format is 32 bpp
[    22.599] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    22.626] (II) NVIDIA(0): Setting mode "DFP-3:nvidia-auto-select"
[    22.783] (==) NVIDIA(0): Disabling shared memory pixmaps
[    22.783] (==) NVIDIA(0): Backing store enabled
[    22.783] (==) NVIDIA(0): Silken mouse enabled
[    22.785] (==) NVIDIA(0): DPMS enabled
[    22.785] (II) Loading sub module "dri2"
[    22.785] (II) LoadModule: "dri2"
[    22.785] (II) Module "dri2" already built-in
[    22.785] (II) NVIDIA(0): [DRI2] Setup complete
[    22.785] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia

---

### Post by kerry_s on 2015-04-18
that is not ubuntu gnome, that is ubuntu unity, the standard ubuntu version.
it says " Virtual screen size determined to be 1280 x 800" that means it's using a scrolling desktop. if you move your mouse to the right & hold it there the whole desktop should scroll.

---

### Post by vettel3 on 2015-04-18
As far as I know it's gnome compiz with unity plugin set using ccsm. Also I never heard about scrolling desktop and mine is definitely not scrollable.

Edit:
It looks like the bar/panel (that one Im looking for) is not really 'outside' screen but is hidden behind top bar (the visible one, displaying application tag/names).

---

