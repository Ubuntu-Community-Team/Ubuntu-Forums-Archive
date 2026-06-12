---
title: "Can't daisy chain monitors using DisplayPort 1.2 MST + NVIDIA K620"
date: 2018-02-20
forum: Desktop Environments
---

### Post by peter-devoy on 2018-02-20
I bought a third monitor and to increase my productivity but ironically have spent six hours trying to get it to work.  In order to support the extravagance I bought a graphics card which supports the use of upto four displays via DisplayPort Multi-stream Transport.  The graphics card has just one DP output so I am daisy-chaining the monitors using the DP cables which came with them.


**Symptoms**
I experimented with just two monitors for simplicity.  The Dell monitors I am using require DP1.2 to be enabled in their settings menu.  I have have read of chains failing when the monitor terminating the chain has this enabled so I tried all possible combinations:
```


            HDMI Cable
      &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
      &#9474;     DP cable                  &#9474;
      &#9474; &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;             &#9474;
    GFX Card      Monitor A        Monitor B       State
        
                DP1.2 enabled               N/A        Both have picture, desktop extends.
                DP1.2 disabled               N/A          Both have picture, desktop extends.




Daisy-chained configurations (no reboot between changes):


           DP cable           DP cable
        &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
    GFX Card      Monitor A        Monitor B       State
        
                DP1.2 enabled          DP1.2 enabled     A has picture.  B in power saving Mode.
                DP1.2 disabled          DP1.2 enabled     Both stuck in power saving mode.
                DP1.2 disabled          DP1.2 disabled    Both have picture, desktop "mirrored".
                DP1.2 enabled          DP1.2 disabled    * Both have picture, desktop "mirrored" (maybe config reverted?)
                                                        * Screen Display GUI shows no screens.
                                                        * Reboots to blinking cursor (log below).

```                




**Hardware**
* Monitors are Dell UltraSharp U2415
* Graphics card is  "HP"/PNY NVIDIA Quadro K620

**OS**
* Ubuntu 16.04.3 LTS
* 4.4.0-112-generic

**Driver**
* 384.111 from nvidia-384

[IMG]https://i.imgur.com/9MOq5vj.png[/IMG]


I tried with Nouveau and the NVIDIA 340.104 drivers but it did not seem to work.
[B]
Next steps?[/B]
I want to try and update the kernel but I can't afford to risk breaking my system right now so I am going to try Ubuntu 17 on a live USB as a next step. 

Below is the Xorg log from the boot to blinking cursor with the below configuration. Note suspicious line "Timed out waiting for DisplayPort device detection to complete":


```

           DP cable           DP cable
        &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
    GFX Card      Monitor A        Monitor B               
                DP1.2 enabled        DP1.2 disabled    
                                                        

```

```
[    78.158] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[    78.158] X Protocol Version 11, Revision 0
[    78.158] Build Operating System: Linux 4.4.0-97-generic x86_64 Ubuntu
[    78.158] Current Operating System: Linux 3XE-dev 4.4.0-112-generic #135-Ubuntu SMP Fri Jan 19 11:48:36 UTC 2018 x86_64
[    78.158] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-112-generic root=UUID=a1bd929e-52cb-4ec7-aed9-0acc3400525b ro quiet splash vt.handoff=7
[    78.158] Build Date: 13 October 2017  01:57:05PM
[    78.158] xorg-server 2:1.18.4-0ubuntu0.7 (For technical support please see http://www.ubuntu.com/support) 
[    78.158] Current version of pixman: 0.33.6
[    78.158]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    78.158] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    78.158] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Feb 20 14:11:31 2018
[    78.158] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    78.159] (==) No Layout section.  Using the first Screen section.
[    78.159] (==) No screen section available. Using defaults.
[    78.159] (**) |-->Screen "Default Screen Section" (0)
[    78.159] (**) |   |-->Monitor "<default monitor>"
[    78.159] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    78.159] (==) Automatically adding devices
[    78.159] (==) Automatically enabling devices
[    78.159] (==) Automatically adding GPU devices
[    78.159] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    78.159] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    78.159]     Entry deleted from font path.
[    78.159] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    built-ins
[    78.159] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    78.159] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    78.159] (II) Loader magic: 0x55d0ba4f8dc0
[    78.159] (II) Module ABI versions:
[    78.159]     X.Org ANSI C Emulation: 0.4
[    78.159]     X.Org Video Driver: 20.0
[    78.159]     X.Org XInput driver : 22.1
[    78.159]     X.Org Server Extension : 9.0
[    78.160] (++) using VT number 7


[    78.160] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    78.160] (II) xfree86: Adding drm device (/dev/dri/card0)
[    78.161] (--) PCI:*(0:1:0:0) 10de:13bb:103c:1098 rev 162, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xce000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288
[    78.161] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    78.161] (II) "glx" will be loaded by default.
[    78.161] (II) LoadModule: "glx"
[    78.161] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    78.167] (II) Module glx: vendor="NVIDIA Corporation"
[    78.167]     compiled for 4.0.2, module version = 1.0.0
[    78.167]     Module class: X.Org Server Extension
[    78.167] (II) NVIDIA GLX Module  384.111  Tue Dec 19 22:51:13 PST 2017
[    78.167] (==) Matched nvidia as autoconfigured driver 0
[    78.167] (==) Matched nouveau as autoconfigured driver 1
[    78.167] (==) Matched nvidia as autoconfigured driver 2
[    78.167] (==) Matched nouveau as autoconfigured driver 3
[    78.167] (==) Matched modesetting as autoconfigured driver 4
[    78.167] (==) Matched fbdev as autoconfigured driver 5
[    78.167] (==) Matched vesa as autoconfigured driver 6
[    78.167] (==) Assigned the driver to the xf86ConfigLayout
[    78.167] (II) LoadModule: "nvidia"
[    78.167] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    78.168] (II) Module nvidia: vendor="NVIDIA Corporation"
[    78.168]     compiled for 4.0.2, module version = 1.0.0
[    78.168]     Module class: X.Org Video Driver
[    78.168] (II) LoadModule: "nouveau"
[    78.168] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    78.168] (II) Module nouveau: vendor="X.Org Foundation"
[    78.168]     compiled for 1.18.1, module version = 1.0.12
[    78.168]     Module class: X.Org Video Driver
[    78.168]     ABI class: X.Org Video Driver, version 20.0
[    78.168] (II) LoadModule: "modesetting"
[    78.168] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    78.168] (II) Module modesetting: vendor="X.Org Foundation"
[    78.168]     compiled for 1.18.4, module version = 1.18.4
[    78.168]     Module class: X.Org Video Driver
[    78.168]     ABI class: X.Org Video Driver, version 20.0
[    78.168] (II) LoadModule: "fbdev"
[    78.168] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    78.168] (II) Module fbdev: vendor="X.Org Foundation"
[    78.168]     compiled for 1.18.1, module version = 0.4.4
[    78.168]     Module class: X.Org Video Driver
[    78.168]     ABI class: X.Org Video Driver, version 20.0
[    78.168] (II) LoadModule: "vesa"
[    78.169] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    78.169] (II) Module vesa: vendor="X.Org Foundation"
[    78.169]     compiled for 1.18.1, module version = 2.3.4
[    78.169]     Module class: X.Org Video Driver
[    78.169]     ABI class: X.Org Video Driver, version 20.0
[    78.169] (II) NVIDIA dlloader X Driver  384.111  Tue Dec 19 22:25:34 PST 2017
[    78.169] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    78.169] (II) NOUVEAU driver Date:   Tue Dec 8 15:52:25 2015 +1000
[    78.169] (II) NOUVEAU driver for NVIDIA chipset families :
[    78.169]     RIVA TNT        (NV04)
[    78.169]     RIVA TNT2       (NV05)
[    78.169]     GeForce 256     (NV10)
[    78.169]     GeForce 2       (NV11, NV15)
[    78.169]     GeForce 4MX     (NV17, NV18)
[    78.169]     GeForce 3       (NV20)
[    78.169]     GeForce 4Ti     (NV25, NV28)
[    78.169]     GeForce FX      (NV3x)
[    78.169]     GeForce 6       (NV4x)
[    78.169]     GeForce 7       (G7x)
[    78.169]     GeForce 8       (G8x)
[    78.169]     GeForce GTX 200 (NVA0)
[    78.169]     GeForce GTX 400 (NVC0)
[    78.169] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    78.169] (II) FBDEV: driver for framebuffer: fbdev
[    78.169] (II) VESA: driver for VESA chipsets: vesa
[    78.169] (II) Loading sub module "fb"
[    78.169] (II) LoadModule: "fb"
[    78.169] (II) Loading /usr/lib/xorg/modules/libfb.so
[    78.169] (II) Module fb: vendor="X.Org Foundation"
[    78.169]     compiled for 1.18.4, module version = 1.0.0
[    78.169]     ABI class: X.Org ANSI C Emulation, version 0.4
[    78.169] (II) Loading sub module "wfb"
[    78.169] (II) LoadModule: "wfb"
[    78.170] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    78.170] (II) Module wfb: vendor="X.Org Foundation"
[    78.170]     compiled for 1.18.4, module version = 1.0.0
[    78.170]     ABI class: X.Org ANSI C Emulation, version 0.4
[    78.170] (II) Loading sub module "ramdac"
[    78.170] (II) LoadModule: "ramdac"
[    78.170] (II) Module "ramdac" already built-in
[    78.170] (WW) Falling back to old probe method for modesetting
[    78.170] (WW) Falling back to old probe method for fbdev
[    78.170] (II) Loading sub module "fbdevhw"
[    78.170] (II) LoadModule: "fbdevhw"
[    78.170] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    78.170] (II) Module fbdevhw: vendor="X.Org Foundation"
[    78.170]     compiled for 1.18.4, module version = 0.0.2
[    78.170]     ABI class: X.Org Video Driver, version 20.0
[    78.170] (WW) Falling back to old probe method for vesa
[    78.171] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    78.171] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    78.171] (==) NVIDIA(0): RGB weight 888
[    78.171] (==) NVIDIA(0): Default visual is TrueColor
[    78.171] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    78.171] (**) NVIDIA(0): Enabling 2D acceleration
[    88.650] (WW) NVIDIA(GPU-0): Timed out waiting for DisplayPort device detection to
[    88.650] (WW) NVIDIA(GPU-0):     complete.
[    88.651] (--) NVIDIA(0): Valid display device(s) on GPU-0 at PCI:1:0:0
[    88.651] (--) NVIDIA(0):     CRT-0
[    88.651] (--) NVIDIA(0):     DFP-0
[    88.651] (--) NVIDIA(0):     DFP-1
[    88.651] (--) NVIDIA(0):     DFP-2 (boot)
[    88.652] (II) NVIDIA(0): NVIDIA GPU Quadro K620 (GM107GL-A) at PCI:1:0:0 (GPU-0)
[    88.652] (--) NVIDIA(0): Memory: 2097152 kBytes
[    88.652] (--) NVIDIA(0): VideoBIOS: 82.07.b3.00.07
[    88.652] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    98.661] (WW) NVIDIA(GPU-0): Timed out waiting for DisplayPort device detection to
[    98.661] (WW) NVIDIA(GPU-0):     complete.
[    98.663] (--) NVIDIA(GPU-0): CRT-0: disconnected
[    98.663] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[    98.663] (--) NVIDIA(GPU-0): 
[    98.666] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    98.666] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    98.666] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    98.666] (--) NVIDIA(GPU-0): 
[    98.667] (--) NVIDIA(GPU-0): DFP-1: disconnected
[    98.667] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[    98.667] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[    98.667] (--) NVIDIA(GPU-0): 
[    98.667] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    98.667] (--) NVIDIA(GPU-0): DFP-2: Internal DisplayPort
[    98.667] (--) NVIDIA(GPU-0): DFP-2: 960.0 MHz maximum pixel clock
[    98.667] (--) NVIDIA(GPU-0): 
[    98.667] (EE) NVIDIA(0): Failed to assign any connected display devices to X screen 0. 
[    98.667] (EE) NVIDIA(0):     Set AllowEmptyInitialConfiguration if you want the server
[    98.667] (EE) NVIDIA(0):     to start anyway
[    98.667] (EE) NVIDIA(0): Failing initialization of X screen 0
[    98.844] (II) UnloadModule: "nvidia"
[    98.844] (II) UnloadSubModule: "wfb"
[    98.844] (II) UnloadSubModule: "fb"
[    98.844] (EE) Screen(s) found, but none have a usable configuration.
[    98.844] (EE) 
Fatal server error:
[    98.844] (EE) no screens found(EE) 
[    98.844] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    98.844] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    98.844] (EE) 
[    98.845] (EE) Server terminated with error (1). Closing log file.

```

Any suggestions would be much appreciated.

---

### Post by DuckHook on 2018-02-20
This user managed it using Artful and a different HW configuration than yours: [https://ubuntuforums.org/showthread.php?t=2380772](https://ubuntuforums.org/showthread.php?t=2380772)

No guarantees, but a newer HWE stack kernel might work, though I am mindful of your desire not to bork your current install.

Let us know how your Artful experiment goes.

---

### Post by peter-devoy on 2018-02-21
Thanks for your help.  I accidentally downloaded Artful MATE but it did indeed work daisy chaining two (but not three) in the same configuration as that user:

GFX Card ----cable----> Monitor A (DP 1.2 Enabled) ----cable----> Monitor B (DP 1.2 Disabled).

Given that sign of hope I guess the next step would be to try your suggestion... is it as simple as running the following command?

```
[COLOR=#333333][FONT=monospace]sudo apt-get install --install-recommends linux-generic-hwe-1604 xserver-xorg-hwe-16.04[/FONT][/COLOR]
```

My system partition is only 70GB so this would be my plan of action:


[LIST=1]
[*]Create bootable Xenial USB in case anything goes wrong.
[*]Use Disks GUI tool to save image of system partition to external drive.
[*]Update kernel
[*]If fail, boot from USB and use Disks GUI tool to restore partition image.
[/LIST]

Would that be a fairly safe of doing it?

---

### Post by DuckHook on 2018-02-21
> **peter-devoy said:**
> …I accidentally downloaded Artful MATE but it did indeed work daisy chaining two (but not three) in the same configuration as that user:
There's a lot happening behind the scenes with daisy-chaining and the maximum number of monitors you can daisy-chain is dependent on many factors including their resolution and refresh rate. This explanation may help: [https://www.displayport.org/cables/driving-multiple-displays-from-a-single-displayport-output/](https://www.displayport.org/cables/driving-multiple-displays-from-a-single-displayport-output/)
There are other bottlenecks as well, though I am not that familiar with them. I've never daisy-chained monitors.
> …is it as simple as running the following command?

```
sudo apt-get install --install-recommends linux-generic-hwe-1604 xserver-xorg-hwe-16.04
```
Yes, that is the proper command.
> …this would be my plan of action:

[LIST=1]
[*]Create bootable Xenial USB in case anything goes wrong.
[*]Use Disks GUI tool to save image of system partition to external drive.
[*]Update kernel
[*]If fail, boot from USB and use Disks GUI tool to restore partition image.
[/LIST]

Would that be a fairly safe of doing it?

Here's how I would proceed:

[list=1]
[*]You must back up all data first. Please read the link in my sig: **!!BACKUP FIRST!!**
[*]Disable all PPAs. You want to be as close to default condition as possible.
[*]I don't know what GUI partition image tools you are referring to. If you have used them before and are confident that they can restore your current install, then I don't see why not.
[*]If you are really paranoid and have sufficient external storage, you can clone your entire current install using *Clonezilla*. I don't feel this to be necessary, but then, I am confident in my ability to recover from most problems. Everyone's individual mileage varies.
[*]Note any special X settings you have. For example, installing the HWE stack reset my wife's monitor at 100% magnification whereas she likes it at 125%.
[*]Proceed with the upgrade.
[/list]
Let us know how it goes.

---

### Post by peter-devoy on 2018-02-22
> **DuckHook said:**
> There's a lot happening behind the scenes with daisy-chaining and the maximum number of monitors you can daisy-chain is dependent on many factors including their resolution and refresh rate.

Yep, you're quite right.  Assuming I read the spec correctly, the graphics card I picked out should be able to handle it which makes me think it might be a limitation in the Nouveau driver.  We'll see how it goes after the kernel upgrade... maybe the proprietary drivers will work and, if not, can attempt to verify hardware capabilities on Windows or compromise by using the HDMI for the third screen.

> **DuckHook said:**
> I don't know what GUI partition image tools you are referring to.

Ah, I just meant the tool called "Disks" accessible from the launcher if you're running Unity... I'm pretty sure it came bundled with Ubuntu.  On closer inspection I see it is gnome-disks. 

I'll heed your advice and do a files backup as well.  Will post back with results, thanks for the tips!

---

### Post by peter-devoy on 2018-03-02
[I]("https://devtalk.nvidia.com/default/topic/1030588/linux/dell-u2415-connected-to-k620-via-dp1-2-mst-is-blank-driver-384-111-on-ubuntu-16-04/I") happened to be setting up a new Xenial workstation so I put the HWE stack on it and tried the hardware on that.  I did not have the same luck that I did with the Nouveau drivers on Artful but with some fiddling managed to achieve the following close-but-no-cigar configuration:

* Monitor A: Connected to K620 DP out. Operating in DP1.2 mode.
* Monitor B: Connected to Monitor A DP out. Operating in DP1.1a mode but blank.
* Monitor C: Connected to K620 DVI out. Operating on HDMI input.

Laid out as follows:

[A][B][C]

[COLOR=#333333][FONT=DINWebPro]Video:[/FONT][/COLOR][https://youtu.be/qZ4LfXFxtYo](https://youtu.be/qZ4LfXFxtYo)

[COLOR=#333333][FONT=DINWebPro]Screenshot:[/FONT][/COLOR][https://imgur.com/xB4Zm0i](https://imgur.com/xB4Zm0i)

Driver is NVIDIA 384.111 
Kernel is 4.13.0-36-generic

Have posted further details at NVIDIA Developer Forums: [https://devtalk.nvidia.com/default/topic/1030588/linux/dell-u2415-connected-to-k620-via-dp1-2-mst-is-blank-driver-384-111-on-ubuntu-16-04/](https://devtalk.nvidia.com/default/topic/1030588/linux/dell-u2415-connected-to-k620-via-dp1-2-mst-is-blank-driver-384-111-on-ubuntu-16-04/)

Will see if they have anything to say.

---

### Post by peter-devoy on 2018-03-03
Another update. Using driver v390.25 the chained monitor will display a prompt if TTY1-6 is used.  Maybe indicates an X issue?

---

