---
title: "xorg.conf is being reseted everytime i do a reboot"
date: 2009-05-20
forum: General Help
---

### Post by bangsergio on 2009-05-20
Hi There,
first of all i would like to introduce myself, my name is sergio and i'm typping from Germany ):P, i'm quite new to linux/Ubuntu and i would like to apologizefor my Englisch but i promise you guys to do my best.

Now back to my problem:

I'm running Ubuntu 9.04 on an USB thumb with persistent changes everything works fine till yet only with the xorg.conf i'm having some problems, i've/can install my nvidia card and xorg.conf looks great and can also activate ubuntu effects ( like windows shake, etc) after restart gdm, the problem is as soon i restart my notebook no more settings on xorg.conf, taking a look on /etc/X11/ i can see that one backup has been done something like "xorg.conf.20090520..." as soon i "mv /etc/X11/xorg.conf.2009... /etc/X11/xorg.conf" and restart gdm everything is ok. 
My question is what can i do to avoid that after restart ubuntu create a default xorg.conf?
I hope you understand what i mean.

PS: I'm writing from my Ubuntu now :D

Thanks
Sergio

---

### Post by bangsergio on 2009-05-20
BUMP
no one can help me??:sad:

---

### Post by Bender2k14 on 2009-05-20
Are you sure that you successfully created a persistent USB?  There were some bugs introduced into Ubuntu 9.04 Jaunty relating to the creation of the persistent storage that did not exist in Ubuntu 8.10 Intrepid.

There are [several threads discussing the issue]("http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=yxl&q=site%3Aubuntuforums.org+jaunty+persistent+usb&btnG=Search&cts=1242825244544").  Take your pick.

---

### Post by _Purple_ on 2009-05-20
[http://ubuntuforums.org/showpost.php?p=6089763&postcount=8](http://ubuntuforums.org/showpost.php?p=6089763&postcount=8)

---

### Post by bangsergio on 2009-05-20
Hi thanks for replying.
Yes i think i've successfully created a persistent USB bec__ause every changes i've done like language (German), background changes, apps installed, Firefox update, everything stays save only xorg.conf is being reseted to default as soon i reboot.

Please can you guys help me?

---

### Post by bangsergio on 2009-05-20
@ Purple

Would like to try it, tell how should the script looks like and whre should i save him.

Should it look like this?:

#!/bin/sh
echo "cp /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf" > resetNVXorgConf
sudo mv resetNVXorgConf /etc/init.d/
sudo chmod +x /etc/init.d/resetNVXorgConf

Where should i save? /etc/X11/

---

### Post by _Purple_ on 2009-05-20
Please run these commands from terminal
```

sudo nvidia-xconfig
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.nvidia
echo "cp /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf" > resetNVXorgConf
sudo mv resetNVXorgConf /etc/init.d/
sudo chmod +x /etc/init.d/resetNVXorgConf
sudo ln -s ../init.d/resetXorgConf S29resetXorgConf
```

---

### Post by bangsergio on 2009-05-20
> **_Purple_ said:**
> Please run these commands from terminal
```

sudo nvidia-xconfig
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.nvidia
echo "cp /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf" > resetNVXorgConf
sudo mv resetNVXorgConf /etc/init.d/
sudo chmod +x /etc/init.d/resetNVXorgConf
sudo ln -s ../init.d/resetXorgConf S29resetXorgConf
```


Same issue again...
I'm going to do same again.

---

### Post by _Purple_ on 2009-05-20
How about this command
```

sudo ln -s etc/init.d/resetXorgConf S29resetXorgConf
```

---

### Post by bangsergio on 2009-05-20
Hi it's me again,
unfortunately after restart same issue again, i have a default xorg.conf also i have a xorg.conf.nvidia and a xorg.conf.200905...
What can i do?

Thanks

---

### Post by bangsergio on 2009-05-20
> **_Purple_ said:**
> How about this command
```

sudo ln -s etc/init.d/resetXorgConf S29resetXorgConf
```

Also tried with, still the same i'm breaking my head.

---

### Post by bangsergio on 2009-05-20
BUMP

No more ideas??

Sergio

---

### Post by _Purple_ on 2009-05-20
Did you install using "Create a USB start up disk option"?

---

### Post by bangsergio on 2009-05-20
No, i've created USB+persistent with a tool called:
 "U904p" found in _[http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/) _.

---

### Post by bangsergio on 2009-05-21
Bump

Hi guys issue still persists, i've also tryed with Ubuntu option"Create a USB start up disk option", but ubuntu stills creates a default xorg.conf everytimes it restart with or without Purple solution, any ideas???

Thanks 
Sergio

---

### Post by larslarsson on 2009-05-22
Hi,

I don't know if it helps, but I have the same thing. Running from USB (made according to pendrivelinux instructions) and Xorg.conf resets at reboot. (Does not reset at X server start, though.)

I haven't tried "un-resetting" when going to another run-level yet, but I will asap.

Lars

---

### Post by bangsergio on 2009-05-22
Still having issue with xorg.conf, please post some solutions.
Could someone try to create a pen with persistent changes and report  how to (with working xorg.conf).

thanks
Sergio

---

### Post by bangsergio on 2009-05-23
BUMP
Hey guys, i see no one cant help so please close this thread.

---

### Post by larslarsson on 2009-05-24
Hi,

just tried the trick in:
[http://ubuntuforums.org/showpost.php?p=6089763&postcount=8](http://ubuntuforums.org/showpost.php?p=6089763&postcount=8)
and it works for me!

Lars

---

### Post by bangsergio on 2009-05-25
Doesnt works for me, please help me.

I have 2 sticks one i've made under windows, the outher under linux (ubuntu) with 2 partitions (FAT32/ext3) on both same issue with xorg.conf being deleted/reseted on boot.
Tried also both with following trick [http://ubuntuforums.org/showpost.php...63&postcount=8]("http://ubuntuforums.org/showpost.php?p=6089763&postcount=8") still the same.

Please [larslarsson]("http://ubuntuforums.org/member.php?u=838341") could you post your steps.

Thanks 
Sergio

---

### Post by _Purple_ on 2009-05-25
Run these commands in terminal one by one and see if it works:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.nvidia
echo "cp /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf" > resetNVXorgConf
sudo mv resetNVXorgConf /etc/init.d/
sudo update-rc.d resetNVXorgConf defaults
sudo chmod +x /etc/init.d/resetNVXorgConf


```

---

### Post by larslarsson on 2009-05-25
Hi Sergio,

I did the commands in the post I linked to, but I think that post forgot one command: 
you have to cd to /etc/rc2.d before the last line, like this:

***********************************
sudo nvidia-xconfig
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.nvidia
echo "cp /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf" > resetNVXorgConf
sudo mv resetNVXorgConf /etc/init.d/ 
sudo chmod +x /etc/init.d/resetNVXorgConf

cd /etc/rc2.d

sudo ln -s ../init.d/resetXorgConf S29resetXorgConf
***********************************

You can always run the script before reboot (/etc/rc2.d/S29resetXorgConf) to see if the correct file is in /etc/X11/xorg.conf

Lars

---

### Post by Zimmer on 2009-05-25
Anyone read the xorg.0.log to see messages relating to the use of the xorg.conf file ?
It might give you a clue as to why it is being reset...

---

### Post by bangsergio on 2009-05-25
Maybe someone can find why xorg.conf is being deleted/reseted on boot.
xorg.0.log

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux ubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon May 25 23:38:40 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation GeForce 9600M GS rev 161, Mem @ 0xfc000000/16777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(WW) "dri2" will not be loaded unless you've specified it to be loaded elsewhere.
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded even though the default is to disable it.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.44  Mon Mar 23 15:29:02 PST 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  180.44  Mon Mar 23 15:05:32 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 9600M GS (G96) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 1048576 kBytes
(--) NVIDIA(0): VideoBIOS: 62.94.3c.00.45
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 9600M GS at PCI:1:0:0:
(--) NVIDIA(0):     AUO (DFP-0)
(--) NVIDIA(0): AUO (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): AUO (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 800
(--) NVIDIA(0): DPI set to (98, 96); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) NVIDIA(0):     enough to receive ACPI display change hotkey events.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "de"
(**) AT Translated Set 2 keyboard: xkb_layout: "de"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) AT Translated Set 2 keyboard: xkb_options: "lv3:ralt_switch"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event7"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "de"
(**) Video Bus: xkb_layout: "de"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) Video Bus: xkb_options: "lv3:ralt_switch"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device Trust GM-4200 Gamer Optical Mouse
(**) Trust GM-4200 Gamer Optical Mouse: always reports core events
(**) Trust GM-4200 Gamer Optical Mouse: Device: "/dev/input/event5"
(II) Trust GM-4200 Gamer Optical Mouse: Found 6 mouse buttons
(II) Trust GM-4200 Gamer Optical Mouse: Found x and y relative axes
(II) Trust GM-4200 Gamer Optical Mouse: Configuring as mouse
(**) Trust GM-4200 Gamer Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Trust GM-4200 Gamer Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Trust GM-4200 Gamer Optical Mouse" (type: MOUSE)
(**) Trust GM-4200 Gamer Optical Mouse: (accel) keeping acceleration scheme 1
(**) Trust GM-4200 Gamer Optical Mouse: (accel) filter chain progression: 2.00
(**) Trust GM-4200 Gamer Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Trust GM-4200 Gamer Optical Mouse: (accel) set acceleration profile 0
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.99.3
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event9"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad touchpad found

---

### Post by Zimmer on 2009-05-27
The log indicates the system is using xorg.conf  and is not defaulting to a default config.

I can only assume that your changes to xorg.conf are either not saved on the USB stick , or the changes you are making to it have no effect on the system....  

I  suggest that you try to create the USB OS again ensuring you have the working config you wish to use in place and saved to xorg.conf first.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by bangsergio on 2009-05-29
> **_Purple_ said:**
> Run these commands in terminal one by one and see if it works:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.nvidia
echo "cp /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf" > resetNVXorgConf
sudo mv resetNVXorgConf /etc/init.d/
sudo update-rc.d resetNVXorgConf defaults
sudo chmod +x /etc/init.d/resetNVXorgConf


```

Hi guys, thanks for all it worked with this.
I'de to create the USB OS again "first one had some badblocks", now is working fine now!!!

Thanks

PS: **How can i delete Ubuntu install icon on the Desktop "ubiquity --desktop %k gtk_ui", if i try to delete it comes back everytime i boot.**

---

### Post by _Purple_ on 2009-05-29
Try
```
sudo apt-get remove ubiquity
```

---

### Post by bangsergio on 2009-05-29
:popcorn: for all, thanks it works, please close thread!!!

:guitar:@ _Purple_ you are the man.:guitar:

Thanks 
Sergio

---

### Post by Zimmer on 2009-05-29
The only way to mark it SOLVED  at the moment is for you to go and EDIT your opening post and ADD [SOLVED] to the title (use thread tools to edit the title )

---

### Post by _Purple_ on 2009-05-29
bangsergio, glad to know that it worked for you. You can do either what Zimmer has mentioned or add a tag "SOLVED" to this thread by clicking on the "Edit Tags" button at the bottom right corner of this page. :)

---

