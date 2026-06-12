---
title: "max resolution twinview"
date: 2006-07-03
forum: Desktop Environments
---

### Post by erimar77 on 2006-07-03
I'm trying to get the max resolution on both of my 20" Dell LCD's.. however, it's not running each monitor at 1600x1200 like they do when used individually.

I'm assuming since I have two 1600x1200 monitors, i can use 3200x1600 as my max resolution using the twinview.

The latest nvidia drivers are installed.  Here's the errors from my Xorg.0.log

```
(**) NVIDIA(0): TwinView enabled
(**) NVIDIA(0): ConnectedMonitor string: "dfp, dfp"
(**) NVIDIA(0): Use of AGPGART requested
(II) NVIDIA(0): Skipping Power Connector Check.
(WW) NVIDIA(0): Invalid ConnectedMonitor request; request was for 'DFP-0,
(WW) NVIDIA(0):     DFP-1', but the valid display devices are 'CRT-0, CRT-1,
(WW) NVIDIA(0):     DFP-0, TV-0'.
(II) NVIDIA(0): NVIDIA GPU GeForce 6800 at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.41.02.34.15
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6800 at PCI:1:0:0:
(--) NVIDIA(0):     Dell 2001FP (CRT-1)
(--) NVIDIA(0):     Dell 2001FP (DFP-0)
(--) NVIDIA(0): Dell 2001FP (CRT-1): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): Dell 2001FP (DFP-0): 155.0 MHz maximum pixel clock
(--) NVIDIA(0): Dell 2001FP (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Devices: CRT-1, DFP-0
(WW) NVIDIA(0): No valid modes for "3200x1600,3200x1600"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1152x864,1152x864"
(II) NVIDIA(0):     "800x600,800x600"
(II) NVIDIA(0):     "1024x768,1024x768"
(II) NVIDIA(0):     "1280x1024,NULL"
(II) NVIDIA(0):     "1024x768,NULL"
(II) NVIDIA(0): Virtual screen size determined to be 2304 x 1024

```

---

### Post by eltech on 2006-10-22
Im curious.. did you ever figure this one out?

---

### Post by Protoss on 2006-10-26
I'd also like to know if this was ever solved as I am suffering from the same thing.

---

