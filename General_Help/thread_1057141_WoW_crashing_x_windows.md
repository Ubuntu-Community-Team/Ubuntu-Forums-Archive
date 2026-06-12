---
title: "WoW crashing x windows"
date: 2009-02-01
forum: General Help
---

### Post by 10wattmindtrip on 2009-02-01
I'm not sure if this is the right place to ask for help; might be a wine specific issue.

I installed World of Warcraft with the latest version of wine (same issue with previous versions also). I turned off full screen bloom, specular lighting, death effect. All settings are turned down low. I have SET gxApi "opengl" in the Config.wtf, also.

My system is the 9450 quad intel, NVidia 9600 GT with 4gigs of RAM running Ubuntu 8.10 x86 (problem happens on all variants of Ubuntu and 64bit).

When I'm in game sometimes X will just go black, my monitor will go to sleep mode and the fan on my video card will start going over time, almost like the drivers kick out. This only seems to happen when I'm running WoW. Now, I installed both drivers for the video card (173 and 177) and still the same issue occurs. I don't want to go through manual installation of the NVidia 180 drivers, but I think I may try it later.

Has anyone else had this issue? I've searched, and although there are a lot of things posted on XWindows issues, it all turned out to be graphical glitches within the game. I haven't that issue.

Thanks

---

### Post by Crafty Kisses on 2009-02-01
Can you post your X logs?
```
/var/log/xorg.0.log
```

---

### Post by 10wattmindtrip on 2009-02-01
/var/log/Xorg.0.log

```
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-xen i686 Ubuntu
Current Operating System: Linux opiate-desktop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686
Build Date: 29 January 2009  07:43:28PM                                                                  
xorg-server 2:1.5.2-2ubuntu3.00~ppa1 (buildd@rothera.buildd)                                             
        Before reporting problems, check http://wiki.x.org                                               
        to make sure that you have the latest version.                                                   
Module Loader present                                                                                    
Markers: (--) probed, (**) from config file, (==) default setting,                                       
        (++) from command line, (!!) notice, (II) informational,                                         
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.                                    
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Feb  1 14:25:47 2009                                     
(==) Using config file: "/etc/X11/xorg.conf"                                                             
(==) No Layout section.  Using the first Screen section.                                                 
(**) |-->Screen "Default Screen" (0)                                                                     
(**) |   |-->Monitor "Configured Monitor"                                                                
(**) |   |-->Device "Configured Video Device"                                                            
(==) Automatically adding devices                                                                        
(==) Automatically enabling devices                                                                      
(==) No FontPath specified.  Using compiled-in default.                                                  
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.                                       
        Entry deleted from font path.                                                                    
(==) FontPath set to:                                                                                    
        /usr/share/fonts/X11/misc,                                                                       
        /usr/share/fonts/X11/100dpi/:unscaled,                                                           
        /usr/share/fonts/X11/75dpi/:unscaled,                                                            
        /usr/share/fonts/X11/Type1,                                                                      
        /usr/share/fonts/X11/100dpi,                                                                     
        /usr/share/fonts/X11/75dpi,                                                                      
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType                                                 
(==) ModulePath set to "/usr/lib/xorg/modules"                                                                      
(II) Cannot locate a core pointer device.                                                                           
(II) Cannot locate a core keyboard device.                                                                          
(II) The server relies on HAL to provide the list of input devices.                                                 
        If no devices become available, reconfigure HAL or disable AllowEmptyInput.                                 
(II) Open ACPI successful (/var/run/acpid.socket)                                                                   
(II) Loader magic: 0x81d9a40                                                                                        
(II) Module ABI versions:                                                                                           
        X.Org ANSI C Emulation: 0.4                                                                                 
        X.Org Video Driver: 4.1                                                                                     
        X.Org XInput driver : 2.1                                                                                   
        X.Org Server Extension : 1.1                                                                                
        X.Org Font Renderer : 0.6                                                                                   
(II) Loader running on linux                                                                                        
(++) using VT number 7                                                                                              
                                                                                                                    
(--) PCI:*(0@4:0:0) nVidia Corporation G94 [GeForce 9600 GT] rev 161, Mem @ 0xea000000/0, 0xc0000000/0, 0xe8000000/0, I/O @ 0x0000bf00/0, BIOS @ 0x????????/524288                                                                       
(II) System resource ranges:                                                                                        
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]                                                         
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]                                                     
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]                                                     
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                                                     
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]                                                         
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]                                                         
(II) "extmod" will be loaded by default.                                                                            
(II) "dbe" will be loaded by default.                                                                               
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.                       
(II) "freetype" will be loaded by default.                                                                          
(II) "record" will be loaded by default.                                                                            
(II) "dri" will be loaded by default.                                                                               
(II) LoadModule: "glx"                                                                                              

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"            
        compiled for 4.0.2, module version = 1.0.0      
        Module class: X.Org Server Extension            
(II) NVIDIA GLX Module  177.82  Tue Nov  4 14:03:48 PST 2008
(II) Loading extension GLX                                  
(II) LoadModule: "extmod"                                   

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"              
        compiled for 1.5.2, module version = 1.0.0         
        Module class: X.Org Server Extension               
        ABI class: X.Org Server Extension, version 1.1     
(II) Loading extension SHAPE                               
(II) Loading extension MIT-SUNDRY-NONSTANDARD              
(II) Loading extension BIG-REQUESTS                        
(II) Loading extension SYNC                                
(II) Loading extension MIT-SCREEN-SAVER                    
(II) Loading extension XC-MISC                             
(II) Loading extension XFree86-VidModeExtension            
(II) Loading extension XFree86-Misc                        
(II) Loading extension XFree86-DGA                         
(II) Loading extension DPMS                                
(II) Loading extension TOG-CUP                             
(II) Loading extension Extended-Visual-Information         
(II) Loading extension XVideo                              
(II) Loading extension XVideo-MotionCompensation           
(II) Loading extension X-Resource                          
(II) LoadModule: "dbe"                                     

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"              
        compiled for 1.5.2, module version = 1.0.0      
        Module class: X.Org Server Extension            
        ABI class: X.Org Server Extension, version 1.1  
(II) Loading extension DOUBLE-BUFFER                    
(II) LoadModule: "freetype"                             

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 1.5.2, module version = 2.1.0                      
        Module class: X.Org Font Renderer                               
        ABI class: X.Org Font Renderer, version 0.6                     
(II) Loading font FreeType                                              
(II) LoadModule: "record"                                               

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"              
        compiled for 1.5.2, module version = 1.13.0        
        Module class: X.Org Server Extension               
        ABI class: X.Org Server Extension, version 1.1     
(II) Loading extension RECORD                              
(II) LoadModule: "dri"                                     

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"              
        compiled for 1.5.2, module version = 1.0.0      
        ABI class: X.Org Server Extension, version 1.1  
(II) Loading extension XFree86-DRI                      
(II) LoadModule: "nvidia"                               

(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"          
        compiled for 4.0.2, module version = 1.0.0       
        Module class: X.Org Video Driver                 
(II) NVIDIA dlloader X Driver  177.82  Tue Nov  4 13:42:45 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs           
(II) Primary Device is: PCI 04@00:00:0                             
(II) Loading sub module "fb"                                       
(II) LoadModule: "fb"                                              

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"   
        compiled for 1.5.2, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"                         
(II) LoadModule: "wfb"                                

(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"   
        compiled for 1.5.2, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"                      
(II) LoadModule: "ramdac"                             
(II) Module "ramdac" already built-in                 
(II) resource ranges after probing:                   
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]    
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]    
(II) NVIDIA(0): Creating default Display subsection in Screen section
        "Default Screen" for depth/fbbpp 24/32                       
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32                    
(==) NVIDIA(0): RGB weight 888                                       
(==) NVIDIA(0): Default visual is TrueColor                          
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)               
(**) NVIDIA(0): Option "NoLogo" "True"                               
(**) NVIDIA(0): Enabling RENDER acceleration                         
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.                                                 
(II) NVIDIA(0): NVIDIA GPU GeForce 9600 GT (G94) at PCI:4:0:0 (GPU-0)        
(--) NVIDIA(0): Memory: 524288 kBytes                                        
(--) NVIDIA(0): VideoBIOS: 62.94.0d.00.03                                    
(II) NVIDIA(0): Detected PCI Express Link width: 16X                         
(--) NVIDIA(0): Interlaced video modes are supported on this GPU             
(--) NVIDIA(0): Connected display device(s) on GeForce 9600 GT at PCI:4:0:0: 
(--) NVIDIA(0):     Acer AL2616W (DFP-0)                                     
(--) NVIDIA(0): Acer AL2616W (DFP-0): 330.0 MHz maximum pixel clock          
(--) NVIDIA(0): Acer AL2616W (DFP-0): Internal Dual Link TMDS                
(II) NVIDIA(0): Assigned Display Device: DFP-0                               
(==) NVIDIA(0):                                                              
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.                       
(==) NVIDIA(0):                                                               
(II) NVIDIA(0): Validated modes:                                              
(II) NVIDIA(0):     "nvidia-auto-select"                                      
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1200              
(--) NVIDIA(0): DPI set to (85, 82); computed from "UseEdidDpi" X config      
(--) NVIDIA(0):     option                                                    
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.                             
(--) Depth 24 pixmap format is 32 bpp                                         
(II) do I need RAC?  No, I don't.                                             
(II) resource ranges after preInit:                                           
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]                   
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]               
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]               
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]               
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]                   
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]                   
(II) NVIDIA(0): Initialized GPU GART.                                         
(II) NVIDIA(0): Setting mode "nvidia-auto-select"                             
(II) Loading extension NV-GLX                                                 
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized               
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture                 
(==) NVIDIA(0): Backing store disabled                                        
(==) NVIDIA(0): Silken mouse enabled                                          
(II) NVIDIA(0): DPMS enabled                                                  
(II) Loading extension NV-CONTROL                                             
(II) Loading extension XINERAMA                                               
(==) RandR enabled                                                            
(II) Initializing built-in extension MIT-SHM                                  
(II) Initializing built-in extension XInputExtension                          
(II) Initializing built-in extension XTEST                                    
(II) Initializing built-in extension XKEYBOARD                                
(II) Initializing built-in extension XC-APPGROUP                              
(II) Initializing built-in extension SECURITY                                 
(II) Initializing built-in extension XINERAMA                                 
(II) Initializing built-in extension XFIXES                                   
(II) Initializing built-in extension RENDER                                   
(II) Initializing built-in extension RANDR                                    
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 2.0.99
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event3"
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found 8 mouse buttons
(II) Logitech USB Receiver: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event2"
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found 9 mouse buttons
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as mouse
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech USB Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech USB Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech USB Receiver: xkb_layout: "us"
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event1"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech USB Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech USB Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech USB Receiver: xkb_layout: "us"
```

I had to wait for it to crash, sorry for the delay.

---

### Post by Crafty Kisses on 2009-02-01
Do you have desktop effects enabled?

---

### Post by 10wattmindtrip on 2009-02-01
I turned off desktop effects just to be sure it wasn't that. Same issue happens almost immediately in-game.

I have effects enabled right now, though. I'll try again.

---

### Post by Crafty Kisses on 2009-02-01
Have you tried unchecking the "Allow Pixel Shader" option in Wine? See if that makes a difference.

---

### Post by 10wattmindtrip on 2009-02-01
Okay, I disabled desktop effects and have disabled "Allow Pixel Shader" in winecfg previously also. Again, same issue. 3mins in game and then black screen. I did notice, however, the computer becomes locked up. I can't switch to any other consoles or even restart. I have to do a cold restart.

---

### Post by Crafty Kisses on 2009-02-01
See if this thread does anything for you, if not I'll try to help you further: [http://ubuntuforums.org/showthread.php?t=671482](http://ubuntuforums.org/showthread.php?t=671482).

---

### Post by 10wattmindtrip on 2009-02-01
It seems to be working now after I removed the latest winehq sources and installed wine 1.0. 

If it crashes again, I'll try installing the newest nvidia drivers.

thank you very much for the help!

-Cheers

---

### Post by Crafty Kisses on 2009-02-01
No problem, my good friend.

---

### Post by 10wattmindtrip on 2009-02-02
Just to give an update before bed:

After trying that fix from that one thread it seemed to work. However, I was wrong, the problem still persists. 

I installed the latest NVidia drivers 180.22 and the outcome is no different. I'm not sure what the problem really is. 

Cheers.

---

### Post by hajbal92 on 2009-02-02
I play wow also and had the same issue. I asked on wineForum, they told me to use wine 1.0 . Now I am using wine 1.1.13 and it works also flawlessly you can switch also....

---

### Post by 10wattmindtrip on 2009-02-02
I have tried with wine 1.0, 1.1.12, 1.1.13, 1.1.14 with all the same issues. I'm unsure what to do next. Maybe install a different distro to see if the same problem arises?

---

### Post by hajbal92 on 2009-02-02
Lol  we have the sam PC config I am with ubuntu 8.04... and wine 1.1.13

And the wow is the only game that crashes?

---

### Post by 10wattmindtrip on 2009-02-04
I haven't really tried any other games, yet. 

I installed the lastest NVidia drivers, no change.
So, I wanted to try a different distro just in case.. I installed Arch Linux, wine 1.1.14. No change, I still get crashes.

So, I'll try Ubuntu 8.04 once again, see if that does anything different. Otherwise, I'm going to search the wine forums again to find out some kind of solution.

---

