---
title: "Xubuntu login problem"
date: 2009-11-06
forum: Desktop Environments
---

### Post by Sofien_24 on 2009-11-06
Hello,I installed xubuntu 9.10, I had Ubuntu 9.04, but I removed it and I installed the new version. When I write my password, the screen changes and then it begins black and returns to the main menu when it demands again the password. There is not a problem of authentication, but the session doesn't want to open. does any one have an idea? thank you.
this video could help:[http://www.metacafe.com/watch/3689361/xubuntu_9_10_trouble/](http://www.metacafe.com/watch/3689361/xubuntu_9_10_trouble/)

---

### Post by Brandon Williams on 2009-11-06
I had this problem. The only solution I could find was to delete me ~/.config directory, log in, and reconfigure XFCE to get it back to how I like it. I was not able to figure out exactly which configuration setting in the original directory was causing the problem.

---

### Post by Sofien_24 on 2009-11-07
I've done it, and it set up the original config. It's almost caused by a default in the structure of the files . How can we report this problem please?

---

### Post by XubuRoxMySox on 2009-11-07
> **Sofien_24 said:**
> How can we report this problem please?

[This](http://www.xubuntu.org/contribute/qa_bugs_testing) should help.

-Robin

---

### Post by Sofien_24 on 2009-11-07
thank you , as I see you are using xubuntu karmic koala, so didn't you have such a problem?

---

### Post by XubuRoxMySox on 2009-11-07
> **Sofien_24 said:**
> thank you , as I see you are using xubuntu karmic koala, so didn't you have such a problem?

I haven't had any such problem at all, but I figured it's because I chose "login automatically" when I installed Xubuntu.

So just for grins I logged out and back in to see if it would freeze, but it logged me out and back in flawlessly.

Maybe it's an update thing? It showed that I had 23 updates to install right away, and it has updated once more since then. Maybe one of those updates fixed it? I dunno... try running the update manager and see if that changes anything. One of the updates was for Grub, in fact. Maybe that was it...

-Robin

---

### Post by Sofien_24 on 2009-11-08
Yes I tried the update , I choosed the option that  enables other updates and it worked finally. Thank you so much

---

### Post by juntjoo on 2009-11-13
> **Brandon Williams said:**
> I had this problem. The only solution I could find was to delete me ~/.config directory, log in, and reconfigure XFCE to get it back to how I like it. I was not able to figure out exactly which configuration setting in the original directory was causing the problem.

is this safe?  how do i do it?  where do i find it?  i've never really explored the linux file system.

---

### Post by tom4jean on 2009-11-14
I just wanted to report the same problem.
I have a clean install of xubuntu 9.10 and it takes me at least 5-6 times of putting in my password in before I get into the desktop.
Prior to that the screen goes black after each time I put in my password and it looks like I am going to get logged in and then it kicks me out to the log-in screen again.

I do not have any pending updates to install and I have tried switching to automatic login to fix it and I get the same thing. When it is set to automatic log in it kicks out to the log in screen again instead of going to the desktop.

I have used xfce with a few other distros and never had this happen.
And prior to this I had ubuntu 9.10 installed and never had this problem, but I repartitioned and put a clean install of xubuntu on because it ran better on my old computer.

I think it is definitely a bug with xubuntu and I did search through the bugs already submitted and found a couple that are almost the same problem.
One of them was from 2008 and was marked "resolved" after an update of someones system in January fixed it, which is obviously not resolved or has reoccurred. 
And another one was newly submitted and had no replies so I saw no point in submitting another one. I could not figure out from them how to fix it.

I have not tried deleting ~/.config because that sounds a bit too drastic to me. I don't want to break the system.

---

### Post by tom4jean on 2009-11-14
Update.

I changed my software sources to "pre-released updates karmic-proposed" and after updating from that I got a new kernel, a new version of gdm, and a new version of xorg server, among others.
Now my log-in works on the first try.
I have no idea which updated package fixed it or if it was the kernel itself, but it works now.
 :p

---

### Post by XubuRoxMySox on 2009-11-14
> **tom4jean said:**
> Update.

I changed my software sources to "pre-released updates karmic-proposed" and after updating from that I got a new kernel, a new version of gdm, and a new version of xorg server, among others.
Now my log-in works on the first try.
I have no idea which updated package fixed it or if it was the kernel itself, but it works now.
 :p

I'm glad that worked for you! That's kinda sorta like getting your updates early - before they're "official," though, isn't it? It seems kinda high risk! 

I hope [my little nagging issue]("http://https://bugs.launchpad.net/bugs/417778") will be solved by a future update. It could become a show-stopper for me. I'll likely stick with long-term-support releases from now on.

-Robin

---

### Post by inearlygaveup on 2009-11-14
> **tom4jean said:**
> Update.

I changed my software sources to "pre-released updates karmic-proposed" and after updating from that I got a new kernel, a new version of gdm, and a new version of xorg server, among others.
Now my log-in works on the first try.
I have no idea which updated package fixed it or if it was the kernel itself, but it works now.
 :p
Hi tom4jean .....is your system still working ok.
I have just re-installed 9.04 after problems all week.
But if yours is working ok I may give it another go.

---

### Post by tom4jean on 2009-11-15
> **dixiedancer said:**
> I'm glad that worked for you! That's kinda sorta like getting your updates early - before they're "official," though, isn't it? It seems kinda high risk! 
Robin

Yes, I guess it could be bit riskier using the latest packages but I honestly don't have the time or patents to either wait for a fix or try and figure out exactly what was wrong. I was tired of putting in my password over and over, and then I kept  wondering if one of those times it would not let me into the desktop at all!

I have a bad habit of just reformatting and using a different Linux distribution when things go wrong rather then taking the time and the headache of figuring out what the problem is. So, I am not the best example!

I was previously using Archlinux but they use the latest of all packages available and they just updated to the newest Xorg Server 1.7 and it does not work at all with my Nividia graphics driver, and Nvidia has no plans on releasing a driver update that will work.

Ironically, I switched to Xubuntu because they had the older xorg that worked with my driver and seemed more stable!
I have had Archlinux break on me a few times because they are "bleeding edge" and use the newest packages and now I am using the newest packages on xubutu.
But at least it is working.

If a long-term release works for you, you may be better off using one. 
I may think about switching to the long-term release myself if anything else goes wrong.

> **inearlygaveup said:**
> Hi tom4jean .....is your system still working ok.
I have just re-installed 9.04 after problems all week.
But if yours is working ok I may give it another go.

Yes, everything is working fine. I wish I could tell you exactly which package update fixed it but like I said I don't know which one did it. when I updated a bunch of pre-release packages updated with any one of them being the possible culprit.

Tom

---

### Post by Vladimir_S on 2009-11-28
The same problem. At least 2-3 times of putting in my password in before I get into the desktop. Karmic Koala.

---

### Post by tom4jean on 2009-12-07
An update on this, I isolated the problem, at least for my installation. 
I previously posted that updating to the "proposed updates" in software sources fixed it. But, what I missed is that I had also changed screen resolutions sometime then too. 
And now playing around with it I found if my screen resolution is set at 1024x768 it will once again lock up and I have a hard a time logging in.

But when I put it back to the default 1280x1040 I have no problem logging in again.
So the problem has something to do with the resolution changing when GDM (the log in manager) goes into the desktop.
If the resolution is different then default it has a hard time changing to it and kicks you back to the log in screen.

Any developers reading this please take note. I don't know how to fix it other then leave my resolution at 1280x1040 which is really making things look too small on the screen.

I have am using the nvidia 96.xx driver

Tom

---

### Post by inearlygaveup on 2009-12-07
I have done a clean install*a couple of times since my last post.
I always set my resolution to 800 x 600*and set my system to encrypt the disc, at the moment it's the best it has been only asking me to log*in twice.

---

### Post by Vladimir_S on 2009-12-09
Solved for me! There was a problem with detecting parametres of my monitor. TFT Viewsonic, but it recognized by a system as a CRT monitor. So, check var/log/Xorg.0.log, if there "The EDID read for display device CRT-1 is invalid..." You are in same situation. What i've done:

1. installed nvidia drivers for my videocard
2. generated the modeline for my monitor (gtf 1440 900 60) 
3. copy and paste generated modeline to the xorg.conf, Section  "Monitor"
4. add to xorg.conf to Section "Monitor" your range of HorizSync and VertRefresh (you can take this parametres for your monitor from website of 
   manufacturer).
5. restart
6. Very important - after loggin in open terminal and: sudo nvidia-settings  
7. X Server Display Configuration -> Display -> Select your resolution, there must be the same resolution for which you have generated modeline. 
8. Press Apply. If resolution will change and it is everything allright, then press button "Save to X Configuration File". If you doesn`t see    
   any error messages - reboot.

After this NVIDIA driver added lines to section "Screen" in xorg.conf. And now i can loggin in to xfce after the first entering of login and pass. Even x11vnc is working now :-).

---

### Post by alcidespinto on 2009-12-09
I made exactly what you said, but unfortunately that didn't work for me.
Well, for start, I didn't find the error message in the Xorg.0.log, so I assume my error is another.

I have to opt for an extreme solution: uninstall the nvidia driver.
The fact is I solve the problem. Moreover, I also had a problem with the screensaver and the power management which I solved too (sometimes these didn't work).

So, I think my problem is with the nvidia driver. Now all I have to do is live with the default video driver (at least until someone come with a good solution, or Nvidia launches a good driver).

---

### Post by Vladimir_S on 2009-12-09
> **alcidespinto said:**
> I made exactly what you said, but unfortunately that didn't work for me.
Well, for start, I didn't find the error message in the Xorg.0.log, so I assume my error is another.

I have to opt for an extreme solution: uninstall the nvidia driver.
The fact is I solve the problem. Moreover, I also had a problem with the screensaver and the power management which I solved too (sometimes these didn't work).

So, I think my problem is with the nvidia driver. Now all I have to do is live with the default video driver (at least until someone come with a good solution, or Nvidia launches a good driver).

I've installed 195.22 beta. Try it. After install attach your Xorg.0.log and Xorg.0.log.old. Maybe we will find solution for you.

---

### Post by alcidespinto on 2009-12-10
Thanks for you help but unfortunately I can't run this driver because it doen't support my video card (which is a GeForce2 MX/MX400).

Is there any alternative driver?

---

### Post by Vladimir_S on 2009-12-11
> **alcidespinto said:**
> Thanks for you help but unfortunately I can't run this driver because it doen't support my video card (which is a GeForce2 MX/MX400).

Is there any alternative driver?
 There is drivers for your card: [http://www.nvidia.co.uk/page/home.html](http://www.nvidia.co.uk/page/home.html) -> Download Drivers -> Beta and Archived Drivers -> Product Type: Legacy and download driver ver. 96.43.14, release date 18.11.2009. Install it, then do all that i sad in post #17. If there will be a trouble, add your xorg.conf, Xorg.0.log and Xorg.0.log.old

---

### Post by alcidespinto on 2009-12-12
Ok, I installed the driver and, of course, the login problem appeared (7 attempts).
Here are the files you requested.

xorg.conf
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Sun Feb  1 20:21:04 UTC 2009

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Sony CPD-200EST"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 120.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce2 MX/MX 400"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1152x864_75 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

xorg.0.log
```
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux luis-desktop 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686
Kernel command line: root=UUID=a94f2254-16f4-4d59-9483-ff3d1f070fe9 ro quiet splash 
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec 12 11:38:54 2009
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
(--) using VT number 9

(--) PCI:*(0:1:0:0) 10de:0110:14af:7102 nVidia Corporation NV11 [GeForce2 MX/MX 400] rev 161, Mem @ 0xce000000/16777216, 0xc0000000/134217728, BIOS @ 0x????????/65536
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  96.43.13  Thu Jun 25 18:56:56 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
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
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  96.43.13  Thu Jun 25 18:45:26 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
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
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce2 MX/MX 400 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 32768 kBytes
(--) NVIDIA(0): VideoBIOS: 03.11.00.08.00
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are not supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce2 MX/MX 400 at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     Sony CPD-200EST (CRT-0)
(--) NVIDIA(0): Sony CPD-200EST (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): 
(WW) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(WW) NVIDIA(0):     will be used as the requested mode.
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(--) NVIDIA(0): DPI set to (49, 50); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
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
(II) config/hal: Adding input device Sleep Button
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event1"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "pt"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "pt"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "pt"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
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
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event4"
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found scroll wheel(s)
(II) Logitech Optical USB Mouse: Configuring as mouse
(**) Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(**) Logitech Optical USB Mouse: (accel) keeping acceleration scheme 1
(**) Logitech Optical USB Mouse: (accel) filter chain progression: 2.00
(**) Logitech Optical USB Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech Optical USB Mouse: (accel) set acceleration profile 0
(II) Logitech Optical USB Mouse: initialized for relative axes.
(II) NVIDIA(0): Setting mode "640x480d60"
(II) NVIDIA(0): Setting mode "CRT-0:1152x864_75@1152x864+0+0"

```

xorg.0.log.old
```
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux luis-desktop 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686
Kernel command line: root=UUID=a94f2254-16f4-4d59-9483-ff3d1f070fe9 ro quiet splash 
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec 12 11:38:31 2009
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
(--) using VT number 9

(--) PCI:*(0:1:0:0) 10de:0110:14af:7102 nVidia Corporation NV11 [GeForce2 MX/MX 400] rev 161, Mem @ 0xce000000/16777216, 0xc0000000/134217728, BIOS @ 0x????????/65536
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  96.43.13  Thu Jun 25 18:56:56 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
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
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  96.43.13  Thu Jun 25 18:45:26 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
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
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce2 MX/MX 400 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 32768 kBytes
(--) NVIDIA(0): VideoBIOS: 03.11.00.08.00
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are not supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce2 MX/MX 400 at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     Sony CPD-200EST (CRT-0)
(--) NVIDIA(0): Sony CPD-200EST (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): 
(WW) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(WW) NVIDIA(0):     will be used as the requested mode.
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(--) NVIDIA(0): DPI set to (49, 50); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
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
(II) config/hal: Adding input device Sleep Button
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event1"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "pt"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "pt"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "pt"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
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
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event4"
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found scroll wheel(s)
(II) Logitech Optical USB Mouse: Configuring as mouse
(**) Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(**) Logitech Optical USB Mouse: (accel) keeping acceleration scheme 1
(**) Logitech Optical USB Mouse: (accel) filter chain progression: 2.00
(**) Logitech Optical USB Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech Optical USB Mouse: (accel) set acceleration profile 0
(II) Logitech Optical USB Mouse: initialized for relative axes.
(II) NVIDIA(0): Setting mode "640x480d60"

Backtrace:
0: /usr/bin/X(xorg_backtrace+0x3b) [0x8133d6b]
1: /usr/bin/X(xf86SigHandler+0x55) [0x80c7d35]
2: [0xe33400]
3: /usr/bin/X [0x80f99f0]
4: /usr/lib/xorg/modules/drivers//nvidia_drv.so [0x5a080a4]
Saw signal 11.  Server aborting.
(II) Sleep Button: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) Logitech Optical USB Mouse: Close
(II) UnloadModule: "evdev"
 ddxSigGiveUp: Closing log

```

Once again, thanks for your help.

---

### Post by Vladimir_S on 2009-12-12
> **alcidespinto said:**
> Ok, I installed the driver and, of course, the login problem appeared (7 attempts).
Here are the files you requested.

xorg.conf
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Sun Feb  1 20:21:04 UTC 2009

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Sony CPD-200EST"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 120.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce2 MX/MX 400"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1152x864_75 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

xorg.0.log
```
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux luis-desktop 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686
Kernel command line: root=UUID=a94f2254-16f4-4d59-9483-ff3d1f070fe9 ro quiet splash 
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec 12 11:38:54 2009
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
(--) using VT number 9

(--) PCI:*(0:1:0:0) 10de:0110:14af:7102 nVidia Corporation NV11 [GeForce2 MX/MX 400] rev 161, Mem @ 0xce000000/16777216, 0xc0000000/134217728, BIOS @ 0x????????/65536
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  96.43.13  Thu Jun 25 18:56:56 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
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
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  96.43.13  Thu Jun 25 18:45:26 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
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
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce2 MX/MX 400 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 32768 kBytes
(--) NVIDIA(0): VideoBIOS: 03.11.00.08.00
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are not supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce2 MX/MX 400 at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     Sony CPD-200EST (CRT-0)
(--) NVIDIA(0): Sony CPD-200EST (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): 
(WW) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(WW) NVIDIA(0):     will be used as the requested mode.
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(--) NVIDIA(0): DPI set to (49, 50); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
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
(II) config/hal: Adding input device Sleep Button
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event1"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "pt"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "pt"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "pt"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
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
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event4"
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found scroll wheel(s)
(II) Logitech Optical USB Mouse: Configuring as mouse
(**) Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(**) Logitech Optical USB Mouse: (accel) keeping acceleration scheme 1
(**) Logitech Optical USB Mouse: (accel) filter chain progression: 2.00
(**) Logitech Optical USB Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech Optical USB Mouse: (accel) set acceleration profile 0
(II) Logitech Optical USB Mouse: initialized for relative axes.
(II) NVIDIA(0): Setting mode "640x480d60"
(II) NVIDIA(0): Setting mode "CRT-0:1152x864_75@1152x864+0+0"

```

xorg.0.log.old
```
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux luis-desktop 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686
Kernel command line: root=UUID=a94f2254-16f4-4d59-9483-ff3d1f070fe9 ro quiet splash 
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec 12 11:38:31 2009
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
(--) using VT number 9

(--) PCI:*(0:1:0:0) 10de:0110:14af:7102 nVidia Corporation NV11 [GeForce2 MX/MX 400] rev 161, Mem @ 0xce000000/16777216, 0xc0000000/134217728, BIOS @ 0x????????/65536
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  96.43.13  Thu Jun 25 18:56:56 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
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
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  96.43.13  Thu Jun 25 18:45:26 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
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
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce2 MX/MX 400 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 32768 kBytes
(--) NVIDIA(0): VideoBIOS: 03.11.00.08.00
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are not supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce2 MX/MX 400 at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     Sony CPD-200EST (CRT-0)
(--) NVIDIA(0): Sony CPD-200EST (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): 
(WW) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(WW) NVIDIA(0):     will be used as the requested mode.
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(--) NVIDIA(0): DPI set to (49, 50); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
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
(II) config/hal: Adding input device Sleep Button
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event1"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "pt"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "pt"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "pt"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
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
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event4"
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found scroll wheel(s)
(II) Logitech Optical USB Mouse: Configuring as mouse
(**) Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(**) Logitech Optical USB Mouse: (accel) keeping acceleration scheme 1
(**) Logitech Optical USB Mouse: (accel) filter chain progression: 2.00
(**) Logitech Optical USB Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech Optical USB Mouse: (accel) set acceleration profile 0
(II) Logitech Optical USB Mouse: initialized for relative axes.
(II) NVIDIA(0): Setting mode "640x480d60"

Backtrace:
0: /usr/bin/X(xorg_backtrace+0x3b) [0x8133d6b]
1: /usr/bin/X(xf86SigHandler+0x55) [0x80c7d35]
2: [0xe33400]
3: /usr/bin/X [0x80f99f0]
4: /usr/lib/xorg/modules/drivers//nvidia_drv.so [0x5a080a4]
Saw signal 11.  Server aborting.
(II) Sleep Button: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) Logitech Optical USB Mouse: Close
(II) UnloadModule: "evdev"
 ddxSigGiveUp: Closing log

```

Once again, thanks for your help.

I don't see the Modeline in xorg.conf, generated by gtf. Did you do each step from post #17? By the way, next week i'll try myself. I'm already have inno GeForce2 MX 400. It is the only task for me to find in our service centre motherboard with agp slot :-)

---

### Post by alcidespinto on 2009-12-12
I had the gtf line, but it was deleted when I reactivated the nvidia driver. Anyway, this line didn't work when I first activated the nvidia driver.

But one thing I discovered. I don't know if it's important or not, but it's good to mention it.
The refresh rate in the nvidia X server settings is 75Hz, but in the xfce display is 50Hz. The range in each setting don't allow me to put the settings in the same refresh rate.
Is this the problem? What modeline should I generate? With 50 or 75Hz?
The resolution is 1152x864.

---

### Post by Vladimir_S on 2009-12-13
> **alcidespinto said:**
> I had the gtf line, but it was deleted when I reactivated the nvidia driver. Anyway, this line didn't work when I first activated the nvidia driver.

But one thing I discovered. I don't know if it's important or not, but it's good to mention it.
The refresh rate in the nvidia X server settings is 75Hz, but in the xfce display is 50Hz. The range in each setting don't allow me to put the settings in the same refresh rate.
Is this the problem? What modeline should I generate? With 50 or 75Hz?
The resolution is 1152x864.

When it a was an issue on my desktop it was the same with refresh rate. I checked resolution and refresh rate in monitor menu. And now, after solved problem it is the same resolution and refresh rate in nvidia X server settings, in xfce display and even in monitor menu. I read manual for your monitor. And i offer to try play with 1024 768 85. By the way, before installing the nvidia driver, be sure that you had uninstalled all old drivers:
1. sudo apt-get --purge remove nvidia-glx nvidia-glx-legacy nvidia-glx-new nvidia-settings

2. check there are no extraneous packages left installed on your system: dpkg -l | grep nvidia  

3. install drivers step by step here (post #1): [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978) post

4. step by step post #17 in this thread.

Good luck, man! And, please, don't forget to post here about results :-)

---

### Post by doctorV23 on 2009-12-13
Similar experience here. This is my (tried and true) take on the solution:

I installed the new Xubuntu on an old machine as a low memory system using the 'alternate install'. It went fine, except that upon rebooting the system and entering the password on the login screen, it cycled back to the login screen instead of going to the desktop making the system unusable.
The fix:
1. Before the login screen displays, press Ctrl+Alt+F1 to bring up a text prompt.
2. Here you should be able to successfully enter your username and password.
3. Type and enter "startx" to bring up that annoyingly illusive desktop!
4. Go to System->Update manager->"Settings..." and add "Prereleased updates karmic proposed".
5. Install all missing updates.
6. Enjoy :-)

---

### Post by clayzermk1 on 2010-01-05
> **doctorV23 said:**
> Similar experience here. This is my (tried and true) take on the solution:

I installed the new Xubuntu on an old machine as a low memory system using the 'alternate install'. It went fine, except that upon rebooting the system and entering the password on the login screen, it cycled back to the login screen instead of going to the desktop making the system unusable.
The fix:
1. Before the login screen displays, press Ctrl+Alt+F1 to bring up a text prompt.
2. Here you should be able to successfully enter your username and password.
3. Type and enter "startx" to bring up that annoyingly illusive desktop!
4. Go to System->Update manager->"Settings..." and add "Prereleased updates karmic proposed".
5. Install all missing updates.
6. Enjoy :-)

With a similar method I was able to get into the xfce desktop (thank you for the suggestion), however, I was unable to remedy the login issue with the above method.

The method I used just to access the desktop was:
1) once the login screen appears, ctrl+alt+f1, login as your user
2) sudo stop gdm
3) sudo startx

From there I was on wifi and had to reenter the key for my router (because you will be running as "root" and there isn't a config yet).

The login issue remains unsolved for me.

Thanks for all your help.:)

---

### Post by somakd on 2010-01-09
I faced the same problem... Actually my initial screen resolution was 800x640 (which is horrible :P). So after logging in I changed my resolution to 1024x768. This worked fine. But I was not able to relogin..each time I tried to login I was re-directed to the login window.  I deleted the ~/.config directory and could log in again but with 800x640 screen resolution. I guess it's a problem with the graphics driver.

anyways xubuntu sucks!!! It's not light-weight at all. :(

---

### Post by XubuRoxMySox on 2010-01-09
> **somakd said:**
> 
anyways xubuntu sucks!!! It's not light-weight at all. :(

I guess it depends on what you're comparing it with. Compared to vanilla Ubuntu, Xubuntu rocks (on my machine at least)! It is free of all that buggy PulseAudio and Mono stuff, and runs faster on that old 'puter than even Crunchbang did!

It's an **[COLOR="Blue"]eye-of-the-beholder[/COLOR]** kinda thing. I think that Ubuntu's effort to be all things to all users is the reason for complaints about "bloat" and "weight" from more experienced Linux users. Linux is ordinarily not a one-size-fits-all kinda thing. But Windows is, and MacOS is. Newbies coming from those backgrounds find 'buntu very appealing. It makes Linux look good to a newbie! And this li'l non-geeky semi-newbie is only just learning that Linux can be anything I want it to be, as much or as little as I like. Compared with Ubuntu, Xubuntu is a *lot* lighter and faster, but still offers the simplicity of Gnome-buntu.

On my laptop I have a much more minimal Linux. But on a shared desktop 'puter that is used by several users (mostly kids), Xubuntu offers a fast, intuitive, "familiar" looking desktop that requires no coaching. They don't even know they're using Linux. And I don't tell them unless someone asks. 

For those who are interested, Xubuntu is simple and easy enough for even a kid to install, so I always keep a few Xubuntu discs around to pass the joy along to other kids and their families.

[COLOR="Blue"][SIZE="6"]Xubuntu rawks![/SIZE][/COLOR]

-Robin

---

