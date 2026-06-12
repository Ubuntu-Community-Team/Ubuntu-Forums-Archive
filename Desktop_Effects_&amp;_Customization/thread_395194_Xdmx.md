---
title: "Xdmx"
date: 2007-03-27
forum: Desktop Effects &amp; Customization
---

### Post by netham45 on 2007-03-27
Ok, I want to use Xdmx over my network with xinerama. I can get Xdmx to go over my network perfectly, but as soon as I turn on xinerama, it spits back errors. I've pasted the stuff it outputs.

root@netham45-ubuntu:~# Xdmx +xinerama :1 -display 192.168.1.100:0.0 -display :2 -input :2
(II) dmx: Generation:         1
(II) dmx: DMX version:        1.2.20040630 (DMX Project)
(II) dmx: DMX Build OS:       Linux (Ubuntu)
(II) dmx: DMX Build Compiler: gcc 4.1.2
(II) dmx: DMX Execution OS:   Linux 2.6.20-12-generic #2 SMP Wed Mar 21 20:55:46 UTC 2007
(II) dmx: DMX Execution Host: netham45-ubuntu
(II) dmx: MAXSCREENS:         16
(II) dmx: Using configuration from command line
(II) dmx: Added 192.168.1.100:0.0 at 0 0
(II) dmx: Added :2 right of 192.168.1.100:0.0
(II) dmx[o0/192.168.1.100:0.0]: Name of display: 192.168.1.100:0.0
(II) dmx[o0/192.168.1.100:0.0]: Version number:  11.0
(II) dmx[o0/192.168.1.100:0.0]: Vendor string:   DECWINDOWS compatibility. Hummingbird Communications Ltd.
(II) dmx[o0/192.168.1.100:0.0]: Vendor release:  7100
(II) dmx[o0/192.168.1.100:0.0]: Dimensions:      1024x768 pixels
(II) dmx[o0/192.168.1.100:0.0]: 4 depths on screen 0:  1,8,12,24
(II) dmx[o0/192.168.1.100:0.0]: Depth of root window:  24 planes (24)
(II) dmx[o0/192.168.1.100:0.0]: Number of colormaps:   8183 min, 8183 max
(II) dmx[o0/192.168.1.100:0.0]: Options: backing-store when mapped, save-unders no
(II) dmx[o0/192.168.1.100:0.0]: Window Manager running: no
(II) dmx[o0/192.168.1.100:0.0]: 1024x768+0+0 on 1024x768 at depth=24, bpp=32
(II) dmx[o0/192.168.1.100:0.0]: 0x21 PseudoColor  8b 8b/rgb 256 0x0000 0x0000 0x0000
(II) dmx[o0/192.168.1.100:0.0]: 0x22 PseudoColor 12b 8b/rgb 4096 0x0000 0x0000 0x0000
(II) dmx[o0/192.168.1.100:0.0]: 0x23 TrueColor   24b 8b/rgb 256 0x00ff 0xff00 0xff0000 *
(II) dmx[o1/:2]: Name of display: :2.0
(II) dmx[o1/:2]: Version number:  11.0
(II) dmx[o1/:2]: Vendor string:   The X.Org Foundation
(II) dmx[o1/:2]: Vendor release:  70200000
(II) dmx[o1/:2]: Dimensions:      1024x768 pixels
(II) dmx[o1/:2]: 7 depths on screen 0:  24,1,4,8,15,16,32
(II) dmx[o1/:2]: Depth of root window:  24 planes (24)
(II) dmx[o1/:2]: Number of colormaps:   1 min, 1 max
(II) dmx[o1/:2]: Options: backing-store no, save-unders no
(II) dmx[o1/:2]: Window Manager running: no
(II) dmx[o1/:2]: 1024x768+0+0 on 1024x768 at depth=24, bpp=32
(II) dmx[o1/:2]: 0x23 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff *
(II) dmx[o1/:2]: 0x24 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x25 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x26 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x27 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x28 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x29 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x2a TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x2b DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x2c DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x2d DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x2e DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x2f DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x30 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x31 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x32 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x4b TrueColor   32b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/192.168.1.100:0.0]: DPMS not supported
(II) dmx[o1/:2]: DPMS 1.1 (on, enabled, 1200 1800 2400)
(II) dmx[o0/192.168.1.100:0.0]: (request) s=1024x768+0+0 r=1024x768+0+0 @0,0 (0) (be=1024x768 depth=24 bpp=32)
(II) dmx[o1/:2]: (request) s=1024x768+0+0 r=1024x768+0+0 @0,0 (1) (be=1024x768 depth=24 bpp=32)
(II) dmx[o0/192.168.1.100:0.0]: s=1024x768+0+0 r=1024x768+0+0 @0,0 (be=1024x768 depth=24 bpp=32)
(II) dmx[o1/:2]: s=1024x768+0+0 r=1024x768+0+0 @1024,0 (be=1024x768 depth=24 bpp=32)
(II) dmx: Using 2048x768 as global bounding box
(II) dmx: XSync batching with 100 ms interval
(II) dmx: Shadow framebuffer support disabled
(II) dmx[i0/:2]: Using backend input from :2
(II) dmx[i0/:2]: Locating devices on :2 (XInputExtension version 1.3)
(II) dmx[i0/:2]:    4 Configured XPointer
(II) dmx[i0/:2]:    0 Synaptics  XExtensionDevice
(II) dmx[i0/:2]:    5 Generic Ke XKeyboard
(II) dmx[i0/:2]:    3 stylus     XExtensionDevice
(II) dmx[i0/:2]:    2 cursor     XExtensionDevice
(II) dmx[i0/:2]:    1 eraser     XExtensionDevice
(II) dmx[i0/:2]: Added backend-mou as pointer device called Mouse0 [core]
(II) dmx[i0/:2]: Added backend-kbd as keyboard device called Keyboard0 [core]
(II) dmx[i0/:2]: Added common-oth as extension device called Other0
(II) dmx[i0/:2]: Added common-oth as extension device called Other1
(II) dmx[i0/:2]: Added common-oth as extension device called Other2
(II) dmx[i0/:2]: Added common-oth as extension device called Other3
(II) dmx[i0/:2]: Using Keyboard0 and Mouse0 as true core devices
(II) dmx[i0/:2]: XKEYBOARD: Defaults: xfree86 us pc101
(II) dmx[i0/:2]: XKEYBOARD: Defaults: xfree86 us pc101
(II) dmx[i0/:2]: XKEYBOARD: Defaults: xfree86 us pc101
(II) dmx[i0/:2]: XKEYBOARD: keycodes = xfree86+aliases(qwerty)
(II) dmx[i0/:2]: XKEYBOARD: symbols  = pc(pc105)+us+level3(ralt_switch)
(II) dmx[i0/:2]: XKEYBOARD: geometry = pc(pc105)
(II) dmx[i0/:2]: XKEYBOARD: From device: xfree86 pc(pc105)+us+level3(ralt_switch) pc(pc105)
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(**) dmx: dmxErrorHandler: BadDevice, invalid or uninitialized input device
(**) dmx:                  Major opcode: 147 (XInputExtension)
(**) dmx:                  Minor opcode: 3 (X_OpenDevice)
(**) dmx:                  ResourceID:   0x0
(**) dmx:                  Failed serial number:  717
(**) dmx:                  Current serial number: 717
(**) dmx: Cannot open eraser device (id=1) on :2
(**) dmx: dmxErrorHandler: BadDevice, invalid or uninitialized input device
(**) dmx:                  Major opcode: 147 (XInputExtension)
(**) dmx:                  Minor opcode: 3 (X_OpenDevice)
(**) dmx:                  ResourceID:   0x0
(**) dmx:                  Failed serial number:  718
(**) dmx:                  Current serial number: 718
(**) dmx: Cannot open cursor device (id=2) on :2
(**) dmx: dmxErrorHandler: BadDevice, invalid or uninitialized input device
(**) dmx:                  Major opcode: 147 (XInputExtension)
(**) dmx:                  Minor opcode: 3 (X_OpenDevice)
(**) dmx:                  ResourceID:   0x0
(**) dmx:                  Failed serial number:  719
(**) dmx:                  Current serial number: 719
(**) dmx: Cannot open stylus device (id=3) on :2
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
(II) dmx: ===== Start of Summary =====
(II) dmx: 2 screens configured with Xinerama (2048 768)
(II) dmx: 0 visuals at depth 1:
(II) dmx: 0 visuals at depth 8:
(II) dmx: 0 visuals at depth 24:
(II) dmx: 6 devices:
(II) dmx:   Id  Name                 Classes
(II) dmx:    0  Mouse0               val btn fb/ptr     [i0/:2/id4=Configured Mouse] core
(II) dmx:    1  Keyboard0            key foc fb/kbd     [i0/:2/id5=Generic Keyboard] core
(II) dmx:    2  Other0               val btn fb/ptr     [i0/:2/id0=Synaptics Touchpad] extension
(II) dmx:    3  Other1               key foc fb/kbd     [i0/:2/id3=stylus] extension
(II) dmx:    4  Other2               key foc fb/kbd     [i0/:2/id2=cursor] extension
(II) dmx:    5  Other3               key foc fb/kbd     [i0/:2/id1=eraser] extension
(II) dmx: ===== End of Summary =====
(!!) dmx: The default visual for screen #0 does not match any of the
(!!) dmx: consolidated visuals from Xinerama (listed above)
(!!) dmx: The default visual for screen #1 does not match any of the
(!!) dmx: consolidated visuals from Xinerama (listed above)
(Fatal Error) dmx: dmxConnectionBlockCallback: invalid screen(s) found
root@netham45-ubuntu:~#


Any help would be welcome. Thanks.

Also, Screen #0 is an X server(Exceed) running on Windows, can't get Linux installed on it because 256MB of ram isn't enough to get going on the LiveCD apparantly.

---

### Post by netham45 on 2007-03-28
*bump*

---

