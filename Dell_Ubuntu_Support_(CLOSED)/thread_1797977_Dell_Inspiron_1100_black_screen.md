---
title: "Dell Inspiron 1100 black screen"
date: 2011-07-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by goodbye-windows(tm) on 2011-07-05
Greetings all,
 

 I am new to ubuntu, and look forward to the day when I can give windows the boot forever.
 

 I have ubuntu running on my desktop computer, and have had it on the Internet. So far, so good.
 

 My problem is converting the Dell laptop over to ubuntu. I have a Dell Inspiron 1100 with windows XP Pro, 750 megabytes of ram and service pack #3. I just checked the bios revision, I have the latest bios (A32) and it runs in windows without issues (other than being nearly unbearably slow::>).
 

 I am trying to run the current version of ubuntu (11-04), not the older versions.
 

 The issue is the video, I get nothing but a black screen when I try to load ubuntu. I believe ubuntu is running, even though the screen shows black. Even with a black screen, I can enter my password and and hearing the Linux sound. I can exit from ubuntu normally (by typing blindly, without the benefit of seeing the screen graphics)....... By that, I mean I can type blindly and ubuntu shuts down in about 3 seconds.
 

 I did buy a 120 GB drive for the laptop, which will be ubuntu only. But for now, I am running a dual boot system on the stock 30 GB hard drive. Whether I use the small dual boot hard drive, or the new 120 GB ubuntu only drive, the problem is the same.
 

 Once in awhile, it will boot normally, not sure how or why this happens. But, it is not consistent.
 

 I did make the cd, and can load ubuntu from the cd, or from the hard drive. When booting from the cd, ubuntu loads normally (most of the time), but it never loads consistently.
 

 I have confirmed that the laptop is not trying to send video to the connector on the back panel.
 

 I can boot into the recovery mode, and I get the command line ok. But, I don't know much about operating from the command line.  
 

 The only indication of an error said ubuntu couldn't recognize the video setup, and I was asked to configure it manually. I did so, and saved the changes, ubuntu indicated it would use this these parameters from now on. But, when trying to boot later, my screen stayed black. Note that this error only happened once-and hasn't recurred.
 

 I also get a low battery indication, which is likely bogus. Not sure why, but it tries to tell me my battery is defective (reading 28.6%).
 

 I have never had an internet connection during the install, but I don't think this should NOT be a problem at this point-my desk top install went well without the internet connection.
 

 My nephew found an ubuntu forum post that seemed to address this exact issue, but the editing of one of the system files (as explained in the message) did not fix the problem. The post he found was written for much older versions of ubuntu, so that might explain why the post from the ubuntu forum archive didn't work for me.
 

 Suggestions and guidance are welcomed. I am no computer expert-so don't get too technical unless it's absolutely necessary.
 

 Thanks,
 
Art

---

### Post by lidex on 2011-07-09
Can you post these outputs please:
```
cat /var/log/Xorg.0.log
```
```
cat /etc/X11/xorg.conf
```
```
sudo lshw -C display
```

---

### Post by goodbye-windows(tm) on 2011-07-13
I'll get the requested output and post it later today.

Here is some additional information that might or might not be helpful.

When I look at the monitor configuration, it shows as being grayed out-so no changes can be made. The configuration shown is correct, except the refresh rate shows as 'zero hertz'-and of course, it cannot be changed. This condition never changes and is not intermittent.

Also, when the video does display, it is often not available when the laptop has been sitting and has turned off the monitor (timed out). When the monitor times out, the screen goes black and nothing short of a reboot will restore it. Note that this is also intermittent-sometimes the video is displayed ok when any key is depressed or the mouse is moved.

Standby for command line output data.......

Art

---

### Post by goodbye-windows(tm) on 2011-07-13
There was a problem with the buffer size in the command line output buffer. The output from the first command creates more lines than the capacity of the buffer can display. I changed the capacity to 5000 lines, and the output still had the beginning cut off. 

I had to change the buffer capacity to 'unlimited', so the length of the file is large.

I hope the large file size does not create problems when posting to the forum.

I'm new, sorry................

Thanks,

Art

-------------------------------------------------------------------

Here goes:


```
:
---------
cat /var/log/Xorg.0.log

art@ubuntu:~$ cat /var/log/Xorg.0.log
[    42.375] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    42.375] X Protocol Version 11, Revision 0
[    42.375] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    42.375] Current Operating System: Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[    42.375] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=802C15FB2C15ECC2 loop=/ubuntu/disks/root.disk ro quiet splash
[    42.380] Build Date: 19 April 2011  03:33:17PM
[    42.380] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    42.380] Current version of pixman: 0.20.2
[    42.380]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    42.380] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    42.381] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul 13 12:40:15 2011
[    42.383] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    42.384] (==) No Layout section.  Using the first Screen section.
[    42.384] (==) No screen section available. Using defaults.
[    42.384] (**) |-->Screen "Default Screen Section" (0)
[    42.384] (**) |   |-->Monitor "<default monitor>"
[    42.385] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    42.385] (==) Automatically adding devices
[    42.386] (==) Automatically enabling devices
[    42.386] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    42.386]     Entry deleted from font path.
[    42.386] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    42.387]     Entry deleted from font path.
[    42.387] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    42.387]     Entry deleted from font path.
[    42.387] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    42.387]     Entry deleted from font path.
[    42.387] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    42.387]     Entry deleted from font path.
[    42.387] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    42.387] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    42.396] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    42.396] (II) Loader magic: 0x81ffde0
[    42.396] (II) Module ABI versions:
[    42.396]     X.Org ANSI C Emulation: 0.4
[    42.396]     X.Org Video Driver: 10.0
[    42.396]     X.Org XInput driver : 12.3
[    42.396]     X.Org Server Extension : 5.0
[    42.404] (--) PCI:*(0:0:2:0) 8086:2562:1028:0149 rev 3, Mem @ 0xe0000000/134217728, 0xf6f80000/524288
[    42.406] (II) Open ACPI successful (/var/run/acpid.socket)
[    42.406] (II) LoadModule: "extmod"
[    42.424] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    42.425] (II) Module extmod: vendor="X.Org Foundation"
[    42.425]     compiled for 1.10.1, module version = 1.0.0
[    42.425]     Module class: X.Org Server Extension
[    42.426]     ABI class: X.Org Server Extension, version 5.0
[    42.426] (II) Loading extension MIT-SCREEN-SAVER
[    42.426] (II) Loading extension XFree86-VidModeExtension
[    42.426] (II) Loading extension XFree86-DGA
[    42.426] (II) Loading extension DPMS
[    42.426] (II) Loading extension XVideo
[    42.426] (II) Loading extension XVideo-MotionCompensation
[    42.426] (II) Loading extension X-Resource
[    42.426] (II) LoadModule: "dbe"
[    42.427] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    42.435] (II) Module dbe: vendor="X.Org Foundation"
[    42.435]     compiled for 1.10.1, module version = 1.0.0
[    42.435]     Module class: X.Org Server Extension
[    42.435]     ABI class: X.Org Server Extension, version 5.0
[    42.435] (II) Loading extension DOUBLE-BUFFER
[    42.435] (II) LoadModule: "glx"
[    42.436] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    42.437] (II) Module glx: vendor="X.Org Foundation"
[    42.437]     compiled for 1.10.1, module version = 1.0.0
[    42.437]     ABI class: X.Org Server Extension, version 5.0
[    42.437] (==) AIGLX enabled
[    42.438] (II) Loading extension GLX
[    42.438] (II) LoadModule: "record"
[    42.439] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    42.440] (II) Module record: vendor="X.Org Foundation"
[    42.440]     compiled for 1.10.1, module version = 1.13.0
[    42.440]     Module class: X.Org Server Extension
[    42.440]     ABI class: X.Org Server Extension, version 5.0
[    42.440] (II) Loading extension RECORD
[    42.440] (II) LoadModule: "dri"
[    42.441] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    42.442] (II) Module dri: vendor="X.Org Foundation"
[    42.442]     compiled for 1.10.1, module version = 1.0.0
[    42.442]     ABI class: X.Org Server Extension, version 5.0
[    42.443] (II) Loading extension XFree86-DRI
[    42.443] (II) LoadModule: "dri2"
[    42.450] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    42.451] (II) Module dri2: vendor="X.Org Foundation"
[    42.451]     compiled for 1.10.1, module version = 1.2.0
[    42.451]     ABI class: X.Org Server Extension, version 5.0
[    42.451] (II) Loading extension DRI2
[    42.451] (==) Matched vesa as autoconfigured driver 0
[    42.451] (==) Matched fbdev as autoconfigured driver 1
[    42.452] (==) Assigned the driver to the xf86ConfigLayout
[    42.452] (II) LoadModule: "vesa"
[    42.454] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    42.454] (II) Module vesa: vendor="X.Org Foundation"
[    42.454]     compiled for 1.10.0, module version = 2.3.0
[    42.455]     Module class: X.Org Video Driver
[    42.455]     ABI class: X.Org Video Driver, version 10.0
[    42.455] (II) LoadModule: "fbdev"
[    42.462] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    42.462] (II) Module fbdev: vendor="X.Org Foundation"
[    42.463]     compiled for 1.10.0, module version = 0.4.2
[    42.463]     ABI class: X.Org Video Driver, version 10.0
[    42.463] (II) VESA: driver for VESA chipsets: vesa
[    42.463] (II) FBDEV: driver for framebuffer: fbdev
[    42.463] (++) using VT number 7

[    42.464] (EE) VESA: Kernel modesetting driver in use, refusing to load
[    42.464] (WW) Falling back to old probe method for vesa
[    42.465] (II) Loading sub module "fbdevhw"
[    42.465] (II) LoadModule: "fbdevhw"
[    42.465] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    42.466] (II) Module fbdevhw: vendor="X.Org Foundation"
[    42.466]     compiled for 1.10.1, module version = 0.0.2
[    42.466]     ABI class: X.Org Video Driver, version 10.0
[    42.466] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    42.467] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    42.467] (**) FBDEV(0): claimed PCI slot 0@0:2:0
[    42.467] (II) FBDEV(0): using default device
[    42.470] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    42.470] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    42.471] (==) FBDEV(0): RGB weight 888
[    42.471] (==) FBDEV(0): Default visual is TrueColor
[    42.471] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    42.471] (II) FBDEV(0): hardware: inteldrmfb (video memory: 3072kB)
[    42.471] (II) FBDEV(0): checking modes against framebuffer device...
[    42.471] (II) FBDEV(0): checking modes against monitor...
[    42.471] (--) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
[    42.471] (**) FBDEV(0):  Built-in mode "current"
[    42.476] (==) FBDEV(0): DPI set to (96, 96)
[    42.476] (II) Loading sub module "fb"
[    42.476] (II) LoadModule: "fb"
[    42.477] (II) Loading /usr/lib/xorg/modules/libfb.so
[    42.477] (II) Module fb: vendor="X.Org Foundation"
[    42.478]     compiled for 1.10.1, module version = 1.0.0
[    42.478]     ABI class: X.Org ANSI C Emulation, version 0.4
[    42.478] (**) FBDEV(0): using shadow framebuffer
[    42.478] (II) Loading sub module "shadow"
[    42.478] (II) LoadModule: "shadow"
[    42.479] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    42.479] (II) Module shadow: vendor="X.Org Foundation"
[    42.479]     compiled for 1.10.1, module version = 1.1.0
[    42.482]     ABI class: X.Org ANSI C Emulation, version 0.4
[    42.482] (==) Depth 24 pixmap format is 32 bpp
[    42.528] (==) FBDEV(0): Backing store disabled
[    42.530] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.530] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.530] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.531] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.531] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.531] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.531] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.531] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.531] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.531] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.531] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.536] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.536] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.536] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.536] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.536] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.536] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.537] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.537] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.537] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.537] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.537] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.537] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.537] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.537] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.538] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.538] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.538] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.538] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.538] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.538] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.538] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.539] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.539] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.539] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.539] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.539] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.539] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.539] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.540] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.540] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.540] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.540] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.540] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.540] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.540] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.540] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.541] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.541] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.541] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.541] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.541] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.541] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.541] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.541] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.542] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.542] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.542] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.542] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.542] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.542] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.542] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.542] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.542] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.543] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.543] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.543] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.543] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.543] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.543] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.543] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.549] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.549] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.549] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.549] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.549] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.549] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.549] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.549] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.550] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.550] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.550] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.550] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.550] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.550] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.550] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.550] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.551] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.551] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.551] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.551] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.551] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.551] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.551] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.551] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.560] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.560] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.560] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.560] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.560] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.560] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.560] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.561] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.561] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.561] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.561] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.561] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.561] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.561] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.561] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.562] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.562] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.562] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.562] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.562] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.562] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.562] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.562] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.563] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.563] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.563] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.563] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.563] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.563] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.563] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.563] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.564] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.564] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.564] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.564] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.564] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.564] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.564] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.565] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.565] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.565] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.565] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.565] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.565] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.565] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.565] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.566] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.566] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.566] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.566] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.566] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.566] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.566] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.566] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.567] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.567] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.567] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.567] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.567] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.567] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.567] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.567] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.572] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.572] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.572] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.573] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.573] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.573] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.573] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.573] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.573] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.573] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.573] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.574] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.574] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.574] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.574] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.574] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.574] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.574] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.574] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.575] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.575] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.575] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.575] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.575] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.575] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.575] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.575] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.580] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.580] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.580] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.580] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.580] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.580] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.580] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.581] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.581] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.581] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.581] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.581] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.581] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.581] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.581] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.582] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.582] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.582] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.582] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.582] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.582] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.582] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.582] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.583] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.583] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.583] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.583] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.583] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.583] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.583] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.583] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.588] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.588] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.588] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.588] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.588] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.588] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.588] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    42.591] (==) FBDEV(0): DPMS enabled
[    42.591] (==) RandR enabled
[    42.591] (II) Initializing built-in extension Generic Event Extension
[    42.591] (II) Initializing built-in extension SHAPE
[    42.591] (II) Initializing built-in extension MIT-SHM
[    42.591] (II) Initializing built-in extension XInputExtension
[    42.591] (II) Initializing built-in extension XTEST
[    42.591] (II) Initializing built-in extension BIG-REQUESTS
[    42.596] (II) Initializing built-in extension SYNC
[    42.596] (II) Initializing built-in extension XKEYBOARD
[    42.596] (II) Initializing built-in extension XC-MISC
[    42.596] (II) Initializing built-in extension SECURITY
[    42.596] (II) Initializing built-in extension XINERAMA
[    42.596] (II) Initializing built-in extension XFIXES
[    42.596] (II) Initializing built-in extension RENDER
[    42.596] (II) Initializing built-in extension RANDR
[    42.596] (II) Initializing built-in extension COMPOSITE
[    42.596] (II) Initializing built-in extension DAMAGE
[    42.596] (II) Initializing built-in extension GESTURE
[    42.647] (II) AIGLX: Screen 0 is not DRI2 capable
[    42.647] (II) AIGLX: Screen 0 is not DRI capable
[    42.647] (II) AIGLX: Trying DRI driver /usr/lib/dri/swrast_dri.so
[    42.694] (II) AIGLX: Loaded and initialized swrast
[    42.694] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    42.759] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    42.859] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    42.859] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    42.865] (II) LoadModule: "evdev"
[    42.867] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    42.870] (II) Module evdev: vendor="X.Org Foundation"
[    42.870]     compiled for 1.10.0.902, module version = 2.6.0
[    42.870]     Module class: X.Org XInput Driver
[    42.870]     ABI class: X.Org XInput driver, version 12.3
[    42.871] (II) Using input driver 'evdev' for 'Video Bus'
[    42.871] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    42.871] (**) Video Bus: always reports core events
[    42.871] (**) Video Bus: Device: "/dev/input/event5"
[    42.877] (--) Video Bus: Found keys
[    42.877] (II) Video Bus: Configuring as keyboard
[    42.877] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input5/event5"
[    42.877] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    42.878] (**) Option "xkb_rules" "evdev"
[    42.878] (**) Option "xkb_model" "pc105"
[    42.878] (**) Option "xkb_layout" "us"
[    42.941] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    42.941] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    42.941] (II) Using input driver 'evdev' for 'Power Button'
[    42.941] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    42.941] (**) Power Button: always reports core events
[    42.942] (**) Power Button: Device: "/dev/input/event1"
[    42.942] (--) Power Button: Found keys
[    42.942] (II) Power Button: Configuring as keyboard
[    42.942] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    42.942] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    42.942] (**) Option "xkb_rules" "evdev"
[    42.943] (**) Option "xkb_model" "pc105"
[    42.943] (**) Option "xkb_layout" "us"
[    42.952] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    42.952] (II) No input driver/identifier specified (ignoring)
[    42.954] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    42.954] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    42.955] (II) Using input driver 'evdev' for 'Sleep Button'
[    42.955] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    42.955] (**) Sleep Button: always reports core events
[    42.955] (**) Sleep Button: Device: "/dev/input/event2"
[    42.955] (--) Sleep Button: Found keys
[    42.962] (II) Sleep Button: Configuring as keyboard
[    42.962] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    42.962] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    42.962] (**) Option "xkb_rules" "evdev"
[    42.962] (**) Option "xkb_model" "pc105"
[    42.963] (**) Option "xkb_layout" "us"
[    43.004] (II) config/udev: Adding input device Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) (/dev/input/event4)
[    43.004] (**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Applying InputClass "evdev pointer catchall"
[    43.004] (II) Using input driver 'evdev' for 'Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)'
[    43.005] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    43.005] (**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): always reports core events
[    43.005] (**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Device: "/dev/input/event4"
[    43.005] (--) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Found 9 mouse buttons
[    43.006] (--) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Found scroll wheel(s)
[    43.006] (--) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Found relative axes
[    43.006] (--) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Found x and y relative axes
[    43.006] (II) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Configuring as mouse
[    43.006] (II) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Adding scrollwheel support
[    43.006] (**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): YAxisMapping: buttons 4 and 5
[    43.006] (**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    43.007] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input4/event4"
[    43.007] (II) XINPUT: Adding extended input device "Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)" (type: MOUSE)
[    43.007] (II) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): initialized for relative axes.
[    43.007] (**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): (accel) keeping acceleration scheme 1
[    43.008] (**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): (accel) acceleration profile 0
[    43.008] (**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): (accel) acceleration factor: 2.000
[    43.008] (**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): (accel) acceleration threshold: 4
[    43.010] (II) config/udev: Adding input device Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) (/dev/input/mouse0)
[    43.010] (II) No input driver/identifier specified (ignoring)
[    43.139] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    43.141] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    43.142] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    43.142] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    43.142] (**) AT Translated Set 2 keyboard: always reports core events
[    43.142] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    43.142] (--) AT Translated Set 2 keyboard: Found keys
[    43.143] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    43.143] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    43.143] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    43.143] (**) Option "xkb_rules" "evdev"
[    43.143] (**) Option "xkb_model" "pc105"
[    43.143] (**) Option "xkb_layout" "us"
[    43.147] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[    43.147] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    43.147] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    43.147] (II) LoadModule: "synaptics"
[    43.161] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    43.162] (II) Module synaptics: vendor="X.Org Foundation"
[    43.162]     compiled for 1.10.0.902, module version = 1.3.99
[    43.162]     Module class: X.Org XInput Driver
[    43.162]     ABI class: X.Org XInput driver, version 12.3
[    43.163] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    43.163] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    43.163] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    43.163] (**) Option "Device" "/dev/input/event6"
[    43.163] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    43.169] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    43.169] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    43.169] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    43.169] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    43.169] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    43.169] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    43.169] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event6"
[    43.170] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    43.170] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    43.170] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    43.170] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    43.171] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    43.171] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    43.171] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    43.171] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    43.176] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[    43.176] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    43.178] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    43.178] (II) No input driver/identifier specified (ignoring)
art@ubuntu:~$ 


---------



```
---------

art@ubuntu:~$ cat /etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: No such file or directory

---------


Code:
---------


art@ubuntu:~$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:11 memory:e0000000-e7ffffff memory:f6f80000-f6ffffff
---------

---

### Post by Lurch310 on 2011-07-15
I have pretty much the same problems with a Dell Inspiron 1100.  Ubuntu worked very well from the CD, but after installation on the HD it only uses the upper left quadrant of the screen and runs very slowly.  Subsequent reboots from the CD have given mixed results.  When it works it works well, but black screens are sometimes the only result.  It doesn't recogize the monitor either way, but uses the full screen when booting from the CD.  Inspiron has a 256 and a 512 memory module.  Anyone have any ideas?  Thanks.

---

### Post by tmittelstaedt on 2011-07-28
I'm posting this message from one of these laptops running the current LTS

The problem is the mode setting on the video chip.  This happens under DOS/Windows too, it is just that the circumstances that create the problem don't often happen.  If you want to see it, then setup a DOS partition
that immediately runs a DOS graphical program as the first statement of the autoexec.

What is going on is that the Dell laptop boots with the Dell graphical splash screen then immediately runs your DOS graphical screen program while the screen is in graphical mode.  You will get garbage on the screen.

With Ubuntu you have to do the following:

1) If your dual-booting between XP and Ubuntu, never do a warm-boot.  Always shut down the system and turn it off, then back on before selecting to go into Ubuntu.

2) Turn off the splash screen by doing the following:

edit menu.lst (per instructions from [http://ubuntuforums.org/showthread.php?p=6000430):](http://ubuntuforums.org/showthread.php?p=6000430):)
   vim +89 /boot/grub/menu.lst
   Change the line: # defoptions=quiet splash
   to read: # defoptions=vga=773 quiet nosplash

Note this is incomplete because on new ubuntu running grub2 you
have to edit /etc/default/grup and then run update-grub

Also you do not need to put the vga=773 in there in the newer Ubuntu because you
want the accellerated drivers.

There is other things to try here:

[http://ubuntuforums.org/showthread.php?t=807351](http://ubuntuforums.org/showthread.php?t=807351)

3) When booting and it goes to the grub screen, DON'T slap Enter immediately, give it a few seconds in
character mode.

Basically to fix the problem what needs to happen is after the machine fires up, it needs to switch to
character mode before switching into graphical mode, and there needs to be a few seconds in
character mode so that your absolutely assured that the mode-set BIOS code has finished executing.

Then when X starts it has to switch from character mode to X Windows.  Having X start while the system is
displaying a graphic image on the screen is sure to trigger the bug.

Older Ubuntu systems used 2D drivers for this video chip, not the 3D drivers and the 2D drivers aren't
bothered by the bug.

Also, TURN OFF the screensaver, or at least set it to blank the screen or not come on for 5 hours or so.  Note that some of the animated screensavers like Ant will cause the system to crash.

---

### Post by goodbye-windows(tm) on 2011-08-02
I changed to Xubuntu, it's better suited for older processors, and it runs a better with less ram.

I do not have a file called  menu.lst in my grub folder.

And I do not have an x11 folder in my etc folder.

Not sure whether the structure is differennt due to the new os, or whether it is different because I am now running Xubuntu.

Any other suggestions?

Thanks,

Art

---

### Post by Toz on 2011-08-03
> **goodbye-windoze said:**
> I changed to Xubuntu, it's better suited for older processors, and it runs a better with less ram.
Welcome to Xubuntu!

> I do not have a file called  menu.lst in my grub folder.
The file to edit is /etc/default/grub (followed by a "sudo update-grub" to commit the changes). The line to edit starts with "GRUB_CMDLINE_LINUX_DEFAULT"

> And I do not have an x11 folder in my etc folder.
The folder is X11 (that's a captial X) in the /etc tree.

> Not sure whether the structure is differennt due to the new os, or whether it is different because I am now running Xubuntu.
The base systems are very similar. The desktop environment and the supporting applications are different.

---

### Post by BBQdave on 2011-08-06
I'm running Ubuntu 10.04 LTS on a dell inspiron 1100 with 1g of memory.  Solid and stable, with my heavily used applications kept current through PPA's.

With your bios updated (A32), I also recommend setting your bios start memory (sorry I'm not sure exactly what it is labeled) to 8mb (the default is 1mb).  You can access that by entering into your bios at start up.  It seems to help, or at least appears to provide a smoother start up into Ubuntu.

Here is a link to how I adjusted start up graphics and solved my black screen problem.  Not sure how it will work with the latest Ubuntu release... but again, I recommend Ubuntu 10.04 LTS, solid great desktop for older hardware.

[http://ubuntuforums.org/showthread.php?t=1785611](http://ubuntuforums.org/showthread.php?t=1785611)

---

### Post by BBQdave on 2011-08-06
To clarify: it is your UMA video memory in the bios.  Standard setting is 1mb.  I increased it to 8mb, which appears to improve start up (into Ubuntu 10.04 LTS).  Again, you can access your bios at start up by pressing F2.

---

### Post by T J Wells on 2011-10-20
I have a Dell Inspiron 1100 with 512 of ram.  It too does not like Ubuntu 11.04 or 11.10 and uses 640 x 480 resolution.

Linux Mint 10.0 and Linux Mint Debian work well at 1024 x 768.  Linux Mint 11.0 is based on Ubuntu 11.04 and it has the same problem as Ubuntu 11.04.

---

