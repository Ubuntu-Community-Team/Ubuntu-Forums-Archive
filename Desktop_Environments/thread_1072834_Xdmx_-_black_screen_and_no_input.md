---
title: "Xdmx - black screen and no input"
date: 2009-02-17
forum: Desktop Environments
---

### Post by cantorman on 2009-02-17
After spending some time poring over the documentation, the forums, googling stuff (I've done my due diligence), I've made it to a certain point in setting up Xdmx and can't get any further.  Maybe it's a bug.  Maybe there's a secret I need to learn.

I've got a dell 650 and a dell 690, each running intrepid, each with dual monitor support, and I'd like to get Xdmx running and managing all 4 monitors.  Not there yet.

My first goal is to get Xdmx to manage two Xnest servers running inside the 690.  The 690 is running xinerama just fine.  I can get two Xnests running inside that, on :1 and :2, and that works.  When I fire up Xdmx I get either an immediate shutdown if I don't say "-shadowfb" or the server up and running, but nothing going on - no display, no input accepted that I can see.

Any takers?

Here's what I've got.

start up Xnest:

xnest.sh
```
#!/bin/bash
startx ./client "$1" -- /usr/bin/Xnest "$1"
```

client:
```
#!/bin/bash
export DISPLAY="$1"
xhost +
/usr/bin/xterm
```

I start up two Xnest servers as follows:

```

./xnest :1 &
./xnest :2 &

```

and I get them, plain, but each with an xterm inside it.

Then I run the xdmx script called "server":
server:
```
#!/bin/bash
startx /usr/bin/xterm -display "$3" -- /usr/bin/Xdmx "$3" -display "$1" -display "$2" -shadowfb
```

Hoping for a single spanning server, I invoke:

```
./server :1 :2 :3
```

I get two black screens that I can't seem to do anything with.  I can use :3 as the display for various programs, but can't see anything.

Lots of output on the invoking window on startup:
```

(II) dmx: Generation:         1
(II) dmx: DMX version:        1.2.20070424 (DMX Project)
(II) dmx: DMX Build OS:       Linux 2.6.24-19-server i686 (Ubuntu)
(II) dmx: DMX Build Compiler: gcc 4.3.2
(II) dmx: DMX Execution OS:   Linux 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009
(II) dmx: DMX Execution Host: probably
(II) dmx: MAXSCREENS:         16
(II) dmx: Using configuration from command line
(II) dmx: Added :1 at 0 0
(II) dmx: Added :2 right of :1
(II) dmx[o0/:1]: No Xdmx server running on backend
(II) dmx[o0/:1]: Name of display: :1.0
(II) dmx[o0/:1]: Version number:  11.0
(II) dmx[o0/:1]: Vendor string:   The X.Org Foundation
(II) dmx[o0/:1]: Vendor release:  10502000
(II) dmx[o0/:1]: Dimensions:      2400x900 pixels
(II) dmx[o0/:1]: 2 depths on screen 0:  1,24
(II) dmx[o0/:1]: Depth of root window:  24 planes (24)
(II) dmx[o0/:1]: Number of colormaps:   1 min, 1 max
(II) dmx[o0/:1]: Options: backing-store no, save-unders no
(II) dmx[o0/:1]: Window Manager running: no
(II) dmx[o0/:1]: 2400x900+0+0 on 2400x900 at depth=24, bpp=32
(II) dmx[o0/:1]: 0x20 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff *
(II) dmx[o0/:1]: 0x21 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x45 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x46 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x47 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x48 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x49 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x4a TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x4b TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x4c TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x4d TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x4e TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x4f TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x50 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x51 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x52 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x53 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x54 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x55 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x56 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x57 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x58 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x59 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x5a DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x5b DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x5c DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x5d DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x5e DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x5f DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x60 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x61 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x62 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x63 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: 0x64 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: No Xdmx server running on backend
(II) dmx[o1/:2]: Name of display: :2.0
(II) dmx[o1/:2]: Version number:  11.0
(II) dmx[o1/:2]: Vendor string:   The X.Org Foundation
(II) dmx[o1/:2]: Vendor release:  10502000
(II) dmx[o1/:2]: Dimensions:      2400x900 pixels
(II) dmx[o1/:2]: 2 depths on screen 0:  1,24
(II) dmx[o1/:2]: Depth of root window:  24 planes (24)
(II) dmx[o1/:2]: Number of colormaps:   1 min, 1 max
(II) dmx[o1/:2]: Options: backing-store no, save-unders no
(II) dmx[o1/:2]: Window Manager running: no
(II) dmx[o1/:2]: 2400x900+0+0 on 2400x900 at depth=24, bpp=32
(II) dmx[o1/:2]: 0x20 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff *
(II) dmx[o1/:2]: 0x21 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x45 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x46 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x47 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x48 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x49 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x4a TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x4b TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x4c TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x4d TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x4e TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x4f TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x50 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x51 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x52 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x53 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x54 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x55 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x56 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x57 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x58 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x59 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x5a DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x5b DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x5c DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x5d DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x5e DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x5f DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x60 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x61 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x62 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x63 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/:2]: 0x64 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:1]: DPMS not supported
(II) dmx[o1/:2]: DPMS not supported
(II) dmx[o0/:1]: (request) s=2400x900+0+0 r=2400x900+0+0 @0,0 (0) (be=2400x900 depth=24 bpp=32)
(II) dmx[o1/:2]: (request) s=2400x900+0+0 r=2400x900+0+0 @0,0 (1) (be=2400x900 depth=24 bpp=32)
(II) dmx[o0/:1]: s=2400x900+0+0 r=2400x900+0+0 @0,0 (be=2400x900 depth=24 bpp=32)
(II) dmx[o1/:2]: s=2400x900+0+0 r=2400x900+0+0 @2400,0 (be=2400x900 depth=24 bpp=32)
(II) dmx: Using 4800x900 as global bounding box
(II) dmx: XSync batching with 100 ms interval
(II) dmx: Shadow framebuffer support enabled
(II) dmx: screen0 FBConfig 0x25 matched to  0x25 on screen#1
(II) dmx: screen0 FBConfig 0x26 matched to  0x26 on screen#1
(II) dmx: screen0 FBConfig 0x27 matched to  0x27 on screen#1
(II) dmx: screen0 FBConfig 0x28 matched to  0x28 on screen#1
(II) dmx: screen0 FBConfig 0x29 matched to  0x29 on screen#1
(II) dmx: screen0 FBConfig 0x2a matched to  0x2a on screen#1
(II) dmx: screen0 FBConfig 0x2b matched to  0x2b on screen#1
(II) dmx: screen0 FBConfig 0x2c matched to  0x2c on screen#1
(II) dmx: screen0 FBConfig 0x2d matched to  0x2d on screen#1
(II) dmx: screen0 FBConfig 0x2e matched to  0x2e on screen#1
(II) dmx: screen0 FBConfig 0x2f matched to  0x2f on screen#1
(II) dmx: screen0 FBConfig 0x30 matched to  0x30 on screen#1
(II) dmx: screen0 FBConfig 0x31 matched to  0x31 on screen#1
(II) dmx: screen0 FBConfig 0x32 matched to  0x32 on screen#1
(II) dmx: screen0 FBConfig 0x33 matched to  0x33 on screen#1
(II) dmx: screen0 FBConfig 0x34 matched to  0x34 on screen#1
(II) dmx: screen0 FBConfig 0x35 matched to  0x35 on screen#1
(II) dmx: screen0 FBConfig 0x36 matched to  0x36 on screen#1
(II) dmx: screen0 FBConfig 0x37 matched to  0x37 on screen#1
(II) dmx: screen0 FBConfig 0x38 matched to  0x38 on screen#1
(II) dmx: screen0 FBConfig 0x39 matched to  0x39 on screen#1
(II) dmx: screen0 FBConfig 0x3a matched to  0x3a on screen#1
(II) dmx: screen0 FBConfig 0x3b matched to  0x3b on screen#1
(II) dmx: screen0 FBConfig 0x3c matched to  0x3c on screen#1
(II) dmx: screen0 FBConfig 0x3d matched to  0x3d on screen#1
(II) dmx: screen0 FBConfig 0x3e matched to  0x3e on screen#1
(II) dmx: screen0 FBConfig 0x3f matched to  0x3f on screen#1
(II) dmx: screen0 FBConfig 0x40 matched to  0x40 on screen#1
(II) dmx: screen0 FBConfig 0x41 matched to  0x41 on screen#1
(II) dmx: screen0 FBConfig 0x42 matched to  0x42 on screen#1
(II) dmx: screen0 FBConfig 0x43 matched to  0x43 on screen#1
(II) dmx: screen0 FBConfig 0x44 matched to  0x44 on screen#1
(II) dmx[i0/:1]: Using backend input from :1
(II) dmx[i0/:1]: Locating devices on :1 (XInputExtension version 1.4)
(II) dmx[i0/:1]:    0 Virtual co XKeyboard       
(II) dmx[i0/:1]:    1 Virtual co XPointer        
(II) dmx[i0/:1]:    2            Unknown         
(II) dmx[i0/:1]:    3            Unknown         
(II) dmx[i0/:1]: Added backend-mou as pointer device called Mouse0 [core]
(II) dmx[i0/:1]: Added backend-kbd as keyboard device called Keyboard0 [core]
(II) dmx[i0/:1]: Using Keyboard0 and Mouse0 as true core devices
(II) dmx[i0/:1]: Could not get XKB information
(II) dmx[i0/:1]: XKEYBOARD: Defaults: xfree86 us pc101  
(II) dmx[i0/:1]: Could not get XKB information
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
(EE) config/hal: NewInputDeviceRequest failed
(EE) config/hal: NewInputDeviceRequest failed
(EE) config/hal: NewInputDeviceRequest failed
(EE) config/hal: NewInputDeviceRequest failed

^C
waiting for X server to shut down xterm:  fatal IO error 11 (Resource temporarily unavailable) or KillClient on X server ":3.0"


xinit:  unexpected signal 2.
```

I'd be delighted to hear from anyone, and am willing to go for it in terms of debugging.  I am new to ubuntu but have been doing unix since 1986.

-dave

---

### Post by ondrejch on 2010-02-19
I'd be delighted to hear from someone who got it working as well ...

Here is mine output: ```
o@tpad ~ $ sudo startx /usr/bin/twm  -- /usr/bin/Xdmx :1 -display :0  -display 192.168.1.104:0 -norender +xinerama  -noglxproxy 
xauth:  creating new authority file /home/o/.serverauth.29448

(II) dmx: Generation:         1
(II) dmx: DMX version:        1.2.20070424 (DMX Project)
(II) dmx: DMX Build OS:       Linux 2.6.31-gentoo-r6-o2-dma i686 ()
(II) dmx: DMX Build Compiler: gcc 4.1.2
(II) dmx: DMX Execution OS:   Linux 2.6.31-gentoo-r6-o2-dma #6 SMP PREEMPT Tue Jan 26 06:28:57 EST 2010
(II) dmx: DMX Execution Host: tpad
(II) dmx: MAXSCREENS:         16
(II) dmx: Using configuration from command line
(II) dmx: Added :0 at 0 0
(II) dmx: Added 192.168.1.104:0 right of :0
(II) dmx[o0/:0]: No Xdmx server running on backend
(II) dmx[o0/:0]: Name of display: :0.0
(II) dmx[o0/:0]: Version number:  11.0
(II) dmx[o0/:0]: Vendor string:   The X.Org Foundation
(II) dmx[o0/:0]: Vendor release:  10605000
(II) dmx[o0/:0]: Dimensions:      1680x1020 pixels
(II) dmx[o0/:0]: 7 depths on screen 0:  24,1,4,8,15,16,32
(II) dmx[o0/:0]: Depth of root window:  24 planes (24)
(II) dmx[o0/:0]: Number of colormaps:   1 min, 1 max
(II) dmx[o0/:0]: Options: backing-store no, save-unders no
(II) dmx[o0/:0]: Window Manager running: yes
(**) dmx[o0/:0]: Window manager running -- colormaps not supported
(II) dmx[o0/:0]: 1680x1020+0+0 on 1680x1020 at depth=24, bpp=32
(II) dmx[o0/:0]: 0x21 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff *
(II) dmx[o0/:0]: 0x22 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:0]: 0x7c TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:0]: 0x7d TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:0]: 0x7e DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:0]: 0x7f DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:0]: 0x80 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o0/:0]: 0x73 TrueColor   32b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: No Xdmx server running on backend
(II) dmx[o1/192.168.1.104:0]: Name of display: 192.168.1.104:0.0
(II) dmx[o1/192.168.1.104:0]: Version number:  11.0
(II) dmx[o1/192.168.1.104:0]: Vendor string:   The X.Org Foundation
(II) dmx[o1/192.168.1.104:0]: Vendor release:  10604000
(II) dmx[o1/192.168.1.104:0]: Dimensions:      1280x1024 pixels
(II) dmx[o1/192.168.1.104:0]: 7 depths on screen 0:  24,1,4,8,15,16,32
(II) dmx[o1/192.168.1.104:0]: Depth of root window:  24 planes (24)
(II) dmx[o1/192.168.1.104:0]: Number of colormaps:   1 min, 1 max
(II) dmx[o1/192.168.1.104:0]: Options: backing-store no, save-unders no
(II) dmx[o1/192.168.1.104:0]: Window Manager running: no
(II) dmx[o1/192.168.1.104:0]: 1280x1024+0+0 on 1280x1024 at depth=24, bpp=32
(II) dmx[o1/192.168.1.104:0]: 0x23 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff *
(II) dmx[o1/192.168.1.104:0]: 0x24 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x25 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x26 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x27 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x28 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x29 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x2a TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x2b TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x2c TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x2d TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x2e TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x2f TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x30 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x31 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x32 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x33 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x34 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x35 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x36 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x37 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x38 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x39 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x3a TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x3b TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x3c TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x3d TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x3e TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x3f TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x40 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x41 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x42 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x43 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x44 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x45 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x46 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x47 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x48 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x49 TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x4a TrueColor   24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x4b DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x4c DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x4d DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x4e DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x4f DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x50 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x51 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x52 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x53 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x54 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x55 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x56 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x57 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x58 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x59 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x5a DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x5b DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x5c DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x5d DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x5e DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x5f DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x60 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x61 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x62 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x63 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x64 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x65 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x66 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x67 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x68 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x69 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x6a DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x6b DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x6c DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x6d DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x6e DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x6f DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x70 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x71 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0x72 DirectColor 24b 8b/rgb 256 0xff0000 0xff00 0x00ff
(II) dmx[o1/192.168.1.104:0]: 0xa6 TrueColor   32b 8b/rgb 256 0xff0000 0xff00 0x00ff
giving up.
xinit:  Connection refused (errno 111):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.

```

I did "xhost  + " in both sessions.

---

