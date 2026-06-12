---
title: "Compiz Fusion Effects enabled, but not working."
date: 2011-01-31
forum: Desktop Environments
---

### Post by shwndzzl on 2011-01-31
Not quite sure what could be wrong here. The settings are enabled, but none of the compiz functions are working. The were working on Friday. 

I did some searching but I'm not even sure what the problem is, or how to diagnose it. 
I'm running 10.10, now.. any help is appreciated. Even if you just tell me what I need to be searching for to find a solution.

Thanks!

---

### Post by Krytarik on 2011-02-01
What video card/chip is installed?
What driver are you (usually) running?
How did you install those?

Check what driver is currently in use:
```
lshw -class video
```
Check if direct rendering/hardware acceleration is enabled:
```
sudo apt-get install mesa-utils
glxinfo |grep rendering
```

---

### Post by Forlong on 2011-02-01
You can use [Compiz-Check]("http://ubuntuforums.org/showthread.php?t=799070") to provide these infos

---

### Post by shwndzzl on 2011-02-01
> **Forlong said:**
> You can use [Compiz-Check]("http://ubuntuforums.org/showthread.php?t=799070") to provide these infos


Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RS690M [Radeon X1200 Series]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

shawn@shawn-laptop:~$

---

### Post by shwndzzl on 2011-02-01
> **Krytarik said:**
> What video card/chip is installed?
What driver are you (usually) running?
How did you install those?

Check what driver is currently in use:
```
lshw -class video
```

description: VGA compatible controller
       product: RS690M [Radeon X1200 Series]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=64
       resources: irq:18 memory:f0000000-f7ffffff memory:f8100000-f810ffff ioport:9000(size=256) memory:f8000000-f80fffff


Check if direct rendering/hardware acceleration is enabled:
```
sudo apt-get install mesa-utils
glxinfo |grep rendering
```


Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  icon-aquadreams-theme libglib2.0-bin libglib2.0-dev gnome-aquadreams-theme
  libsqlite3-dev metacity-aquadreams-theme kdesudo wallpaper-aquadreams-theme
  zlib1g-dev libxml2-dev gtk-aquadreams-theme emerald-aquadreams-theme
  update-manager-kde
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  mesa-utils
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 27.0kB of archives.
After this operation, 135kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe mesa-utils i386 8.0.1-0ubuntu1 [27.0kB]
Fetched 27.0kB in 0s (36.2kB/s)
Selecting previously deselected package mesa-utils.
(Reading database ... 196844 files and directories currently installed.)
Unpacking mesa-utils (from .../mesa-utils_8.0.1-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up mesa-utils (8.0.1-0ubuntu1) ...

---

### Post by shwndzzl on 2011-02-01
So I did everything you guys told me.. I didnt understand evertyhing that was going on but from the looks of it. I am ok.. lol. Still no wobbly windows, etc..

---

### Post by Copper Bezel on 2011-02-01
The output you posted was from the installation process of the tool. Run the second line (beginning with "glxinfo") and post that here.

Before you do, though, try [this.]("http://wiki.compiz.org/Hardware/Blacklist")

compiz SKIP_CHECKS=yes

---

### Post by shwndzzl on 2011-02-01
> **Copper Bezel said:**
> The output you posted was from the installation process of the tool. Run the second line (beginning with "glxinfo") and post that here.

Before you do, though, try [this.]("http://wiki.compiz.org/Hardware/Blacklist")

compiz SKIP_CHECKS=yes


:lolflag: I though it was odd.. 

Ran the compiz skip check...

compiz (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz (core) - Fatal: No manageable screens found on display :0.0

thats what I ended up with...
So am I using the wrong window manager?? Seems like an easy fix, but what window manager.

---

### Post by Forlong on 2011-02-01
What's the output of
```
dpkg -l | grep compiz
```

---

### Post by shwndzzl on 2011-02-01
> **Forlong said:**
> What's the output of
```
dpkg -l | grep compiz
```


ii  compiz                                    1:0.8.6-0ubuntu9.1                                OpenGL window and compositing manager
ii  compiz-core                               1:0.8.6-0ubuntu9.1                                OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra               0.8.6-0ubuntu1                                    Collection of extra plugins from OpenCompositing for Compiz
ii  compiz-fusion-plugins-main                0.8.6-0ubuntu2                                    Compiz Fusion plugins - main collection
ii  compiz-gnome                              1:0.8.6-0ubuntu9.1                                OpenGL window and compositing manager - GNOME window decorator
ii  compiz-plugins                            1:0.8.6-0ubuntu9.1                                OpenGL window and compositing manager - plugins
ii  compizconfig-backend-gconf                0.8.4-1ubuntu5                                    Compiz Fusion configuration system - gconf backend
ii  compizconfig-settings-manager             0.8.2-0ubuntu1                                    Compiz configuration settings manager
rc  emerald                                   0.7.2-0ubuntu4                                    Decorator for compiz-fusion
ii  libcompizconfig0                          0.8.4-0ubuntu3                                    Settings library for plugins - OpenCompositing Project
rc  libemeraldengine0                         0.7.2-0ubuntu4                                    Decoration engines for compiz-fusion
ii  python-compizconfig                       0.8.4-2ubuntu2                                    Compizconfig bindings for python

---

### Post by shwndzzl on 2011-02-01
I just gotta say I really appreciate your quick responses, and help guys!

---

### Post by Forlong on 2011-02-01
Did you try to install Compiz manually or by script?

It looks like you are good to go but that Compiz error indicates some kind of an interference. Specifically the replacement of the current window manager - Compiz should do that by default.

What's the output of
```
sudo updatedb && locate bin/compiz
```
as well as
```
compiz --replace
```

---

### Post by Krytarik on 2011-02-01
What *Copper Bezel* actually want you to try is:
```
SKIP_CHECKS=yes compiz --replace
```
instead of just:
```
compiz --replace
```

---

### Post by shwndzzl on 2011-02-01
> **Forlong said:**
> Did you try to install Compiz manually or by script?

It looks like you are good to go but that Compiz error indicates some kind of an interference. Specifically the replacement of the current window manager - Compiz should do that by default.

What's the output of
```
sudo updatedb && locate bin/compiz
```as well as
```
compiz --replace
```



shawn@shawn-laptop:~$ sudo updatedb && locate bin/compiz
[sudo] password for shawn: 
/usr/bin/compiz
/usr/bin/compiz-decorator
shawn@shawn-laptop:~$ compiz --replace
Starting gtk-window-decorator
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

---

### Post by shwndzzl on 2011-02-01
> **Krytarik said:**
> What *Copper Bezel* actually want you to try is:
```
SKIP_CHECKS=yes compiz --replace
```instead of just:
```
compiz --replace
```


So the Compiz --replace some how fixed it...
Everything is working as it used to now.. 

Any ideas why?

---

### Post by Krytarik on 2011-02-01
> **shwndzzl said:**
> So the Compiz --replace some how fixed it...
Everything is working as it used to now.. 

Any ideas why?
See the website, also provided by *Copper Bezel*:
[http://wiki.compiz.org/Hardware/Blacklist](http://wiki.compiz.org/Hardware/Blacklist)

Though your video chip isn't listed in that "blacklist".

Try setting those option as default:
> You can also store this value, where it is depends on your distribution, usually it is a matter of putting

SKIP_CHECKS=yes

in ~/.config/compiz/compiz-manager . 

---

### Post by Forlong on 2011-02-01
It would have been detected by compiz-check, if blacklisted hardware is in use.

As far as I know, compiz-manager is deprecated in Maverick, so setting the SKIP_CHECKS variable has no effect whatsoever.

@shwndzzl: actually, I am curious too. As I said, the compiz binary should utilize the --replace option by default.
What happens when running
```
 metacity --replace & sleep 3 && compiz
```

---

### Post by shwndzzl on 2011-02-10
So I am back.. it looks like it didnt get fixed. its still an issue. 
The following is what I have done since.. Your help is appreciated.



shawn@shawn-laptop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RS690M [Radeon X1200 Series]
 Driver in use:         radeon
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)

---

### Post by shwndzzl on 2011-02-10
> **Forlong said:**
> It would have been detected by compiz-check, if blacklisted hardware is in use.

As far as I know, compiz-manager is deprecated in Maverick, so setting the SKIP_CHECKS variable has no effect whatsoever.

@shwndzzl: actually, I am curious too. As I said, the compiz binary should utilize the --replace option by default.
What happens when running
```
 metacity --replace & sleep 3 && compiz
```


I tried that and got:

metacity --replace & sleep 3 && compiz
[1] 2645
Starting gtk-window-decorator
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

---

### Post by Krytarik on 2011-02-10
How about taking care of this one now!?
> **Krytarik said:**
> What video card/chip is installed?
What driver are you (usually) running?
How did you install those?

I've checked what drivers you can use. For your "legacy" ATI card the best available driver is the Open Source Edge driver:
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers)

If you're not already running those, try uprading to it:
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Copper Bezel on 2011-02-10
> As far as I know, compiz-manager is deprecated in Maverick, so setting the SKIP_CHECKS variable has no effect whatsoever.

Yeah, sorry about that - God, and it was right in the page I linked with everything else. I had a machine with a blacklisted card a year ago or so and had rather taken this for granted, and I only found out in another conversation a few days ago about this change.

---

### Post by Forlong on 2011-02-11
> **shwndzzl said:**
> I tried that and got:

metacity --replace & sleep 3 && compiz
[1] 2645
Starting gtk-window-decorator
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
That means Compiz is in fact running and you're good to go.
Could you please re-download Compiz-Check and run it again? I have updated it, because they seem to have changed something regarding AIGLX.

---

### Post by shwndzzl on 2011-02-11
> **Forlong said:**
> That means Compiz is in fact running and you're good to go.
Could you please re-download Compiz-Check and run it again? I have updated it, because they seem to have changed something regarding AIGLX.


Ran it again..


Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RS690M [Radeon X1200 Series]
 Driver in use:         radeon
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)

---

### Post by shwndzzl on 2011-02-11
> **Krytarik said:**
> How about taking care of this one now!?

I've checked what drivers you can use. For your "legacy" ATI card the best available driver is the Open Source Edge driver:
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers)

If you're not already running those, try uprading to it:
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```


Updated it as directed.. restarted, and no change observed.

---

### Post by Forlong on 2011-02-11
Post your **/var/log/Xorg.0.log** and use the forum's [CODE] tag (# button in the editor) please.

---

### Post by realzippy on 2011-02-11
...if* compiz --replace* fixes it temporarily,add it as command to Startup Applications.

---

### Post by shwndzzl on 2011-02-11
> **Forlong said:**
> Post your **/var/log/Xorg.0.log** and use the forum's ```
 tag (# button in the editor) please.

I was wondering how you guys did that! lol.. this is what I got with /var/log/Xorg.0.log

[CODE]shawn@shawn-laptop:~$ /var/log/Xorg.0.log
bash: /var/log/Xorg.0.log: Permission denied
shawn@shawn-laptop:~$ sudo /var/log/Xorg.0.log
[sudo] password for shawn: 
sudo: /var/log/Xorg.0.log: command not found
shawn@shawn-laptop:~$ 

```

---

### Post by shwndzzl on 2011-02-11
> **realzippy said:**
> ...if* compiz --replace* fixes it temporarily,add it as command to Startup Applications.


I may try that.. FYI this is what I get when I use compiz-replace.
Functions return, but only temporarily. 

```
shawn@shawn-laptop:~$ compiz --replace
r300: DRM version: 2.5.0, Name: ATI RS690, ID: 0x791f, GB: 1, Z: 1
r300: GART size: 509 MB, VRAM size: 128 MB
r300: AA compression: NO, Z compression: NO, HiZ: NO
Starting gtk-window-decorator
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

```

---

### Post by Krytarik on 2011-02-11
*Forlong* meant it more like this ;-):
```
gedit /var/log/Xorg.0.log
```
And please post your "~/.xsession-errors" as well.
```
gedit ~/.xsession-errors
```

---

### Post by realzippy on 2011-02-11
If you run
```
compiz --replace
```
compiz only runs as long the as terminal is opened.

```
compiz --replace &
```
lets you close the terminal compiz still running;however only for this session.
Again,put it in Startup Applications to get compiz after reboot.

---

### Post by shwndzzl on 2011-02-11
> **Krytarik said:**
> *Forlong* meant it more like this ;-):
```
gedit /var/log/Xorg.0.log
```And please post your "~/.xsession-errors" as well.
```
gedit ~/.xsession-errors
```


gedit /var/log/Xorg.0.log 
```
[    27.966] 
X.Org X Server 1.9.2.901 (1.9.3 RC 1)
Release Date: 2010-11-13
[    27.966] X Protocol Version 11, Revision 0
[    27.966] Build Operating System: Linux 2.6.24-28-xen i686 Ubuntu
[    27.966] Current Operating System: Linux shawn-laptop 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686
[    27.966] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-25-generic root=UUID=2485f1a0-e116-49d3-b09c-661d207198b4 ro quiet splash
[    27.967] Build Date: 29 November 2010  03:29:38PM
[    27.967] xorg-server 2:1.9.2.901+git20101129+server-1.9-branch.65f2ab20-0ubuntu0sarvatt2~maverick (For technical support please see http://www.ubuntu.com/support) 
[    27.967] Current version of pixman: 0.21.4
[    27.967]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    27.967] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    27.967] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb 11 09:59:56 2011
[    28.197] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    28.336] (==) No Layout section.  Using the first Screen section.
[    28.336] (==) No screen section available. Using defaults.
[    28.336] (**) |-->Screen "Default Screen Section" (0)
[    28.336] (**) |   |-->Monitor "<default monitor>"
[    28.336] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    28.336] (==) Automatically adding devices
[    28.336] (==) Automatically enabling devices
[    28.363] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    28.363]     Entry deleted from font path.
[    28.443] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    28.443] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    28.443] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    28.443] (II) Loader magic: 0x81fa7c0
[    28.443] (II) Module ABI versions:
[    28.443]     X.Org ANSI C Emulation: 0.4
[    28.443]     X.Org Video Driver: 8.0
[    28.443]     X.Org XInput driver : 11.0
[    28.443]     X.Org Server Extension : 4.0
[    28.444] (--) PCI:*(0:1:5:0) 1002:791f:1179:ff1a rev 0, Mem @ 0xf0000000/134217728, 0xf8100000/65536, 0xf8000000/1048576, I/O @ 0x00009000/256
[    28.444] (II) Open ACPI successful (/var/run/acpid.socket)
[    28.444] (II) LoadModule: "extmod"
[    28.564] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    28.590] (II) Module extmod: vendor="X.Org Foundation"
[    28.590]     compiled for 1.9.2.901, module version = 1.0.0
[    28.590]     Module class: X.Org Server Extension
[    28.590]     ABI class: X.Org Server Extension, version 4.0
[    28.590] (II) Loading extension MIT-SCREEN-SAVER
[    28.590] (II) Loading extension XFree86-VidModeExtension
[    28.590] (II) Loading extension XFree86-DGA
[    28.590] (II) Loading extension DPMS
[    28.590] (II) Loading extension XVideo
[    28.590] (II) Loading extension XVideo-MotionCompensation
[    28.590] (II) Loading extension X-Resource
[    28.590] (II) LoadModule: "dbe"
[    28.590] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    28.604] (II) Module dbe: vendor="X.Org Foundation"
[    28.604]     compiled for 1.9.2.901, module version = 1.0.0
[    28.604]     Module class: X.Org Server Extension
[    28.604]     ABI class: X.Org Server Extension, version 4.0
[    28.604] (II) Loading extension DOUBLE-BUFFER
[    28.604] (II) LoadModule: "glx"
[    28.605] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    28.626] (II) Module glx: vendor="X.Org Foundation"
[    28.626]     compiled for 1.9.2.901, module version = 1.0.0
[    28.626]     ABI class: X.Org Server Extension, version 4.0
[    28.627] (==) AIGLX enabled
[    28.627] (II) Loading extension GLX
[    28.627] (II) LoadModule: "record"
[    28.628] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    28.645] (II) Module record: vendor="X.Org Foundation"
[    28.645]     compiled for 1.9.2.901, module version = 1.13.0
[    28.645]     Module class: X.Org Server Extension
[    28.645]     ABI class: X.Org Server Extension, version 4.0
[    28.645] (II) Loading extension RECORD
[    28.645] (II) LoadModule: "dri"
[    28.645] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    28.646] (II) Module dri: vendor="X.Org Foundation"
[    28.646]     compiled for 1.9.2.901, module version = 1.0.0
[    28.646]     ABI class: X.Org Server Extension, version 4.0
[    28.646] (II) Loading extension XFree86-DRI
[    28.646] (II) LoadModule: "dri2"
[    28.647] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    28.648] (II) Module dri2: vendor="X.Org Foundation"
[    28.648]     compiled for 1.9.2.901, module version = 1.2.0
[    28.648]     ABI class: X.Org Server Extension, version 4.0
[    28.648] (II) Loading extension DRI2
[    28.648] (==) Matched fglrx as autoconfigured driver 0
[    28.648] (==) Matched ati as autoconfigured driver 1
[    28.648] (==) Matched vesa as autoconfigured driver 2
[    28.648] (==) Matched fbdev as autoconfigured driver 3
[    28.648] (==) Assigned the driver to the xf86ConfigLayout
[    28.648] (II) LoadModule: "fglrx"
[    28.649] (WW) Warning, couldn't open module fglrx
[    28.649] (II) UnloadModule: "fglrx"
[    28.649] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    28.649] (II) LoadModule: "ati"
[    28.650] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    28.656] (II) Module ati: vendor="X.Org Foundation"
[    28.656]     compiled for 1.9.2.901, module version = 6.13.99
[    28.656]     Module class: X.Org Video Driver
[    28.656]     ABI class: X.Org Video Driver, version 8.0
[    28.656] (II) LoadModule: "radeon"
[    28.656] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    29.035] (II) Module radeon: vendor="X.Org Foundation"
[    29.035]     compiled for 1.9.2.901, module version = 6.13.99
[    29.035]     Module class: X.Org Video Driver
[    29.035]     ABI class: X.Org Video Driver, version 8.0
[    29.044] (II) LoadModule: "vesa"
[    29.044] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    29.055] (II) Module vesa: vendor="X.Org Foundation"
[    29.055]     compiled for 1.9.2.901, module version = 2.3.0
[    29.055]     Module class: X.Org Video Driver
[    29.055]     ABI class: X.Org Video Driver, version 8.0
[    29.055] (II) LoadModule: "fbdev"
[    29.055] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    29.075] (II) Module fbdev: vendor="X.Org Foundation"
[    29.075]     compiled for 1.8.99.904, module version = 0.4.2
[    29.075]     ABI class: X.Org Video Driver, version 8.0
[    29.075] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
    ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
    ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
    ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
    ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
    ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
    ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
    ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
    ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
    AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
    ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
    ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
    ATI Mobility Radeon HD 4670, ATI FirePro M5750,
    ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
    ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
    ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
    ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
    ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3000 Graphics, ATI Radeon HD 4200, ATI Radeon 4100,
    ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
    ATI Radeon HD 4290, ATI Radeon HD 4250, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6250 Graphics, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5900 Series, ATI Radeon HD 5900 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 5700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
    ATI Mobility Radeon Graphics, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
    ATI Radeon HD 5450, CEDAR, AMD Radeon HD 6900M Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS,
    Mobility Radeon HD 6000 Series, Mobility Radeon HD 6000 Series,
    BARTS, BARTS, BARTS, BARTS, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6800 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS
[    29.085] (II) VESA: driver for VESA chipsets: vesa
[    29.085] (II) FBDEV: driver for framebuffer: fbdev
[    29.085] (++) using VT number 7

[    29.085] (II) [KMS] Kernel modesetting enabled.
[    29.085] (WW) Falling back to old probe method for vesa
[    29.085] (WW) Falling back to old probe method for fbdev
[    29.085] (II) Loading sub module "fbdevhw"
[    29.085] (II) LoadModule: "fbdevhw"
[    29.086] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    29.126] (II) Module fbdevhw: vendor="X.Org Foundation"
[    29.126]     compiled for 1.9.2.901, module version = 0.0.2
[    29.126]     ABI class: X.Org Video Driver, version 8.0
[    29.126] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    29.126] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    29.126] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    29.127] (==) RADEON(0): Default visual is TrueColor
[    29.127] (==) RADEON(0): RGB weight 888
[    29.127] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    29.127] (--) RADEON(0): Chipset: "ATI Radeon X1200" (ChipID = 0x791f)
[    29.127] (II) RADEON(0): PCI card detected
[    29.127] drmOpenDevice: node name is /dev/dri/card0
[    29.127] drmOpenDevice: open result is 9, (OK)
[    29.127] drmOpenByBusid: Searching for BusID pci:0000:01:05.0
[    29.127] drmOpenDevice: node name is /dev/dri/card0
[    29.127] drmOpenDevice: open result is 9, (OK)
[    29.127] drmOpenByBusid: drmOpenMinor returns 9
[    29.127] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    29.127] drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
[    29.127] (II) RADEON(0): KMS Color Tiling: enabled
[    29.127] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    29.292] (II) RADEON(0): Output VGA-0 has no monitor section
[    29.292] (II) RADEON(0): Output LVDS has no monitor section
[    29.436] (II) RADEON(0): Output S-video has no monitor section
[    29.584] (II) RADEON(0): EDID for output VGA-0
[    29.584] (II) RADEON(0): EDID for output LVDS
[    29.584] (II) RADEON(0): Manufacturer: LPL  Model: dc00  Serial#: 0
[    29.584] (II) RADEON(0): Year: 2006  Week: 0
[    29.584] (II) RADEON(0): EDID Version: 1.3
[    29.584] (II) RADEON(0): Digital Display Input
[    29.584] (II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    29.584] (II) RADEON(0): Gamma: 2.20
[    29.584] (II) RADEON(0): No DPMS capabilities specified
[    29.584] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    29.584] (II) RADEON(0): First detailed timing is preferred mode
[    29.584] (II) RADEON(0): redX: 0.600 redY: 0.351   greenX: 0.324 greenY: 0.554
[    29.584] (II) RADEON(0): blueX: 0.153 blueY: 0.145   whiteX: 0.312 whiteY: 0.328
[    29.584] (II) RADEON(0): Manufacturer's mask: 0
[    29.584] (II) RADEON(0): Supported detailed timing:
[    29.584] (II) RADEON(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
[    29.584] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
[    29.584] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
[    29.584] (II) RADEON(0):  LGPhilipsLCD
[    29.584] (II) RADEON(0):  LP154WX4-TLD2
[    29.584] (II) RADEON(0): EDID (in hex):
[    29.584] (II) RADEON(0):     00ffffffffffff00320c00dc00000000
[    29.584] (II) RADEON(0):     00100103802115780ab3409959538d27
[    29.584] (II) RADEON(0):     25505400000001010101010101010101
[    29.584] (II) RADEON(0):     010101010101bc1b00a0502017303020
[    29.584] (II) RADEON(0):     36004bcf100000190000000000000000
[    29.584] (II) RADEON(0):     00000000000000000000000000fe004c
[    29.584] (II) RADEON(0):     475068696c6970734c43440a000000fe
[    29.584] (II) RADEON(0):     004c503135345758342d544c44320043
[    29.584] (II) RADEON(0): Printing probed modes for output LVDS
[    29.584] (II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    29.584] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    29.584] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    29.584] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    29.584] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    29.585] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    29.585] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    29.585] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    29.729] (II) RADEON(0): EDID for output S-video
[    29.729] (II) RADEON(0): Output VGA-0 disconnected
[    29.729] (II) RADEON(0): Output LVDS connected
[    29.729] (II) RADEON(0): Output S-video disconnected
[    29.729] (II) RADEON(0): Using exact sizes for initial modes
[    29.729] (II) RADEON(0): Output LVDS using initial mode 1280x800
[    29.729] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    29.729] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:8000000 visible:7bd8000
[    29.729] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    29.729] (==) RADEON(0): DPI set to (96, 96)
[    29.729] (II) Loading sub module "fb"
[    29.729] (II) LoadModule: "fb"
[    29.729] (II) Loading /usr/lib/xorg/modules/libfb.so
[    29.755] (II) Module fb: vendor="X.Org Foundation"
[    29.755]     compiled for 1.9.2.901, module version = 1.0.0
[    29.755]     ABI class: X.Org ANSI C Emulation, version 0.4
[    29.755] (II) Loading sub module "ramdac"
[    29.755] (II) LoadModule: "ramdac"
[    29.755] (II) Module "ramdac" already built-in
[    29.755] (II) Loading sub module "exa"
[    29.755] (II) LoadModule: "exa"
[    29.756] (II) Loading /usr/lib/xorg/modules/libexa.so
[    29.774] (II) Module exa: vendor="X.Org Foundation"
[    29.774]     compiled for 1.9.2.901, module version = 2.5.0
[    29.774]     ABI class: X.Org Video Driver, version 8.0
[    29.774] (II) UnloadModule: "vesa"
[    29.774] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    29.774] (II) UnloadModule: "fbdev"
[    29.774] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    29.774] (II) UnloadModule: "fbdevhw"
[    29.774] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    29.774] (--) Depth 24 pixmap format is 32 bpp
[    29.774] (II) RADEON(0): [DRI2] Setup complete
[    29.774] (II) RADEON(0): [DRI2]   DRI driver: r300
[    29.775] (II) RADEON(0): Front buffer size: 4000K
[    29.775] (II) RADEON(0): VRAM usage limit set to 110534K
[    29.813] (==) RADEON(0): Backing store disabled
[    29.813] (II) RADEON(0): Direct rendering enabled
[    29.838] (II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
[    29.838] (II) RADEON(0): Setting EXA maxPitchBytes
[    29.838] (II) EXA(0): Driver allocated offscreen pixmaps
[    29.838] (II) EXA(0): Driver registered support for the following operations:
[    29.838] (II)         Solid
[    29.838] (II)         Copy
[    29.838] (II)         Composite (RENDER acceleration)
[    29.838] (II)         UploadToScreen
[    29.838] (II)         DownloadFromScreen
[    29.838] (II) RADEON(0): Acceleration enabled
[    29.838] (==) RADEON(0): DPMS enabled
[    29.838] (==) RADEON(0): Silken mouse enabled
[    29.846] (II) RADEON(0): Set up textured video
[    29.846] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    29.847] (--) RandR disabled
[    29.847] (II) Initializing built-in extension Generic Event Extension
[    29.847] (II) Initializing built-in extension SHAPE
[    29.847] (II) Initializing built-in extension MIT-SHM
[    29.847] (II) Initializing built-in extension XInputExtension
[    29.847] (II) Initializing built-in extension XTEST
[    29.847] (II) Initializing built-in extension BIG-REQUESTS
[    29.847] (II) Initializing built-in extension SYNC
[    29.847] (II) Initializing built-in extension XKEYBOARD
[    29.847] (II) Initializing built-in extension XC-MISC
[    29.847] (II) Initializing built-in extension SECURITY
[    29.847] (II) Initializing built-in extension XINERAMA
[    29.847] (II) Initializing built-in extension XFIXES
[    29.847] (II) Initializing built-in extension RENDER
[    29.847] (II) Initializing built-in extension RANDR
[    29.847] (II) Initializing built-in extension COMPOSITE
[    29.847] (II) Initializing built-in extension DAMAGE
[    29.847] (II) Initializing built-in extension GESTURE
[    30.334] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    30.334] (II) AIGLX: enabled GLX_INTEL_swap_event
[    30.334] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    30.334] (II) AIGLX: enabled GLX_SGI_make_current_read
[    30.334] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    30.335] (II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
[    30.335] (II) GLX: Initialized DRI2 GL provider for screen 0
[    30.354] (II) RADEON(0): Setting screen physical size to 338 x 211
[    30.641] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    30.658] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    30.658] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    30.658] (II) LoadModule: "evdev"
[    30.658] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.688] (II) Module evdev: vendor="X.Org Foundation"
[    30.689]     compiled for 1.9.2.901, module version = 2.5.99
[    30.689]     Module class: X.Org XInput Driver
[    30.689]     ABI class: X.Org XInput driver, version 11.0
[    30.689] (**) Power Button: always reports core events
[    30.689] (**) Power Button: Device: "/dev/input/event2"
[    30.701] (--) Power Button: Found keys
[    30.701] (II) Power Button: Configuring as keyboard
[    30.701] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    30.701] (**) Option "xkb_rules" "evdev"
[    30.701] (**) Option "xkb_model" "pc105"
[    30.701] (**) Option "xkb_layout" "us"
[    30.703] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    30.703] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    30.703] (**) Video Bus: always reports core events
[    30.703] (**) Video Bus: Device: "/dev/input/event7"
[    30.709] (--) Video Bus: Found keys
[    30.709] (II) Video Bus: Configuring as keyboard
[    30.709] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    30.709] (**) Option "xkb_rules" "evdev"
[    30.709] (**) Option "xkb_model" "pc105"
[    30.709] (**) Option "xkb_layout" "us"
[    30.709] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    30.709] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    30.709] (**) Power Button: always reports core events
[    30.709] (**) Power Button: Device: "/dev/input/event0"
[    30.721] (--) Power Button: Found keys
[    30.721] (II) Power Button: Configuring as keyboard
[    30.721] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    30.721] (**) Option "xkb_rules" "evdev"
[    30.721] (**) Option "xkb_model" "pc105"
[    30.721] (**) Option "xkb_layout" "us"
[    30.721] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    30.721] (II) No input driver/identifier specified (ignoring)
[    30.726] (II) config/udev: Adding input device PIXART USB OPTICAL MOUSE (/dev/input/event4)
[    30.726] (**) PIXART USB OPTICAL MOUSE: Applying InputClass "evdev pointer catchall"
[    30.726] (**) PIXART USB OPTICAL MOUSE: always reports core events
[    30.726] (**) PIXART USB OPTICAL MOUSE: Device: "/dev/input/event4"
[    30.741] (--) PIXART USB OPTICAL MOUSE: Found 3 mouse buttons
[    30.741] (--) PIXART USB OPTICAL MOUSE: Found scroll wheel(s)
[    30.741] (--) PIXART USB OPTICAL MOUSE: Found relative axes
[    30.741] (--) PIXART USB OPTICAL MOUSE: Found x and y relative axes
[    30.741] (II) PIXART USB OPTICAL MOUSE: Configuring as mouse
[    30.741] (II) PIXART USB OPTICAL MOUSE: Adding scrollwheel support
[    30.741] (**) PIXART USB OPTICAL MOUSE: YAxisMapping: buttons 4 and 5
[    30.741] (**) PIXART USB OPTICAL MOUSE: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    30.741] (II) XINPUT: Adding extended input device "PIXART USB OPTICAL MOUSE" (type: MOUSE)
[    30.741] (**) PIXART USB OPTICAL MOUSE: (accel) keeping acceleration scheme 1
[    30.741] (**) PIXART USB OPTICAL MOUSE: (accel) acceleration profile 0
[    30.741] (**) PIXART USB OPTICAL MOUSE: (accel) acceleration factor: 2.000
[    30.741] (**) PIXART USB OPTICAL MOUSE: (accel) acceleration threshold: 4
[    30.741] (II) PIXART USB OPTICAL MOUSE: initialized for relative axes.
[    30.741] (II) config/udev: Adding input device PIXART USB OPTICAL MOUSE (/dev/input/mouse0)
[    30.741] (II) No input driver/identifier specified (ignoring)
[    30.742] (II) config/udev: Adding input device Microsoft Wired Keyboard 600 (/dev/input/event5)
[    30.742] (**) Microsoft Wired Keyboard 600: Applying InputClass "evdev keyboard catchall"
[    30.742] (**) Microsoft Wired Keyboard 600: always reports core events
[    30.742] (**) Microsoft Wired Keyboard 600: Device: "/dev/input/event5"
[    30.753] (--) Microsoft Wired Keyboard 600: Found keys
[    30.753] (II) Microsoft Wired Keyboard 600: Configuring as keyboard
[    30.753] (II) XINPUT: Adding extended input device "Microsoft Wired Keyboard 600" (type: KEYBOARD)
[    30.753] (**) Option "xkb_rules" "evdev"
[    30.753] (**) Option "xkb_model" "pc105"
[    30.753] (**) Option "xkb_layout" "us"
[    30.753] (II) config/udev: Adding input device Microsoft Wired Keyboard 600 (/dev/input/event6)
[    30.753] (**) Microsoft Wired Keyboard 600: Applying InputClass "evdev keyboard catchall"
[    30.754] (**) Microsoft Wired Keyboard 600: always reports core events
[    30.754] (**) Microsoft Wired Keyboard 600: Device: "/dev/input/event6"
[    30.769] (--) Microsoft Wired Keyboard 600: Found 1 mouse buttons
[    30.769] (--) Microsoft Wired Keyboard 600: Found scroll wheel(s)
[    30.769] (--) Microsoft Wired Keyboard 600: Found relative axes
[    30.769] (--) Microsoft Wired Keyboard 600: Found absolute axes
[    30.769] (--) Microsoft Wired Keyboard 600: Found x and y absolute axes
[    30.769] (--) Microsoft Wired Keyboard 600: Found keys
[    30.769] (II) Microsoft Wired Keyboard 600: Configuring as mouse
[    30.769] (II) Microsoft Wired Keyboard 600: Configuring as keyboard
[    30.769] (II) Microsoft Wired Keyboard 600: Adding scrollwheel support
[    30.769] (**) Microsoft Wired Keyboard 600: YAxisMapping: buttons 4 and 5
[    30.769] (**) Microsoft Wired Keyboard 600: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    30.769] (II) XINPUT: Adding extended input device "Microsoft Wired Keyboard 600" (type: KEYBOARD)
[    30.769] (**) Option "xkb_rules" "evdev"
[    30.769] (**) Option "xkb_model" "pc105"
[    30.769] (**) Option "xkb_layout" "us"
[    30.769] (EE) Microsoft Wired Keyboard 600: failed to initialize for relative axes.
[    30.769] (WW) Microsoft Wired Keyboard 600: found 37 axes, limiting to 36.
[    30.769] (II) Microsoft Wired Keyboard 600: initialized for absolute axes.
[    30.770] (II) config/udev: Adding input device Microsoft Wired Keyboard 600 (/dev/input/js0)
[    30.770] (II) No input driver/identifier specified (ignoring)
[    30.770] (II) config/udev: Adding input device Chicony USB 2.0 Camera (/dev/input/event8)
[    30.770] (**) Chicony USB 2.0 Camera: Applying InputClass "evdev keyboard catchall"
[    30.770] (**) Chicony USB 2.0 Camera: always reports core events
[    30.770] (**) Chicony USB 2.0 Camera: Device: "/dev/input/event8"
[    30.781] (--) Chicony USB 2.0 Camera: Found keys
[    30.781] (II) Chicony USB 2.0 Camera: Configuring as keyboard
[    30.781] (II) XINPUT: Adding extended input device "Chicony USB 2.0 Camera" (type: KEYBOARD)
[    30.781] (**) Option "xkb_rules" "evdev"
[    30.781] (**) Option "xkb_model" "pc105"
[    30.781] (**) Option "xkb_layout" "us"
[    30.784] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    30.784] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    30.784] (**) AT Translated Set 2 keyboard: always reports core events
[    30.784] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    30.789] (--) AT Translated Set 2 keyboard: Found keys
[    30.789] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    30.789] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    30.789] (**) Option "xkb_rules" "evdev"
[    30.789] (**) Option "xkb_model" "pc105"
[    30.789] (**) Option "xkb_layout" "us"
[    30.789] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event9)
[    30.789] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    30.789] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    30.790] (II) LoadModule: "synaptics"
[    30.790] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    30.814] (II) Module synaptics: vendor="X.Org Foundation"
[    30.814]     compiled for 1.8.99.904, module version = 1.2.99
[    30.814]     Module class: X.Org XInput Driver
[    30.814]     ABI class: X.Org XInput driver, version 11.0
[    30.814] (II) Synaptics touchpad driver version 1.2.99
[    30.814] (**) Option "Device" "/dev/input/event9"
[    30.877] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    30.877] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    30.877] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    30.877] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    30.877] (--) SynPS/2 Synaptics TouchPad: buttons: left right scroll-buttons
[    30.896] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    30.896] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    30.901] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    30.901] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    30.901] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    30.901] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    30.901] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    30.924] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    30.924] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    30.924] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    30.924] (II) Synaptics touchpad driver version 1.2.99
[    31.569] (EE) SynPS/2 Synaptics TouchPad no synaptics event device found
[    31.569] (**) Option "Device" "/dev/input/mouse1"
[    31.601] (EE) Query no Synaptics: 6003C8
[    31.601] (--) SynPS/2 Synaptics TouchPad: no supported touchpad found
[    31.601] (EE) SynPS/2 Synaptics TouchPad Unable to query/initialize Synaptics hardware.
[    31.624] (EE) PreInit failed for input device "SynPS/2 Synaptics TouchPad"
[    31.624] (II) UnloadModule: "synaptics"
[    36.572] (II) RADEON(0): EDID vendor "LPL", prod id 56320
[    36.572] (II) RADEON(0): Printing DDC gathered Modelines:
[    36.572] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    36.865] (II) RADEON(0): EDID vendor "LPL", prod id 56320
[    36.865] (II) RADEON(0): Printing DDC gathered Modelines:
[    36.865] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    37.224] (II) RADEON(0): EDID vendor "LPL", prod id 56320
[    37.224] (II) RADEON(0): Printing DDC gathered Modelines:
[    37.224] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    37.512] (II) RADEON(0): EDID vendor "LPL", prod id 56320
[    37.512] (II) RADEON(0): Printing DDC gathered Modelines:
[    37.512] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    66.784] (II) RADEON(0): EDID vendor "LPL", prod id 56320
[    66.784] (II) RADEON(0): Printing DDC gathered Modelines:
[    66.784] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    67.096] (II) RADEON(0): EDID vendor "LPL", prod id 56320
[    67.096] (II) RADEON(0): Printing DDC gathered Modelines:
[    67.096] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    67.456] (II) RADEON(0): EDID vendor "LPL", prod id 56320
[    67.456] (II) RADEON(0): Printing DDC gathered Modelines:
[    67.456] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    77.393] (II) RADEON(0): EDID vendor "LPL", prod id 56320
[    77.393] (II) RADEON(0): Printing DDC gathered Modelines:
[    77.393] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  7678.788] (II) RADEON(0): EDID vendor "LPL", prod id 56320
[  7678.788] (II) RADEON(0): Printing DDC gathered Modelines:
[  7678.788] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  7828.400] (II) RADEON(0): EDID vendor "LPL", prod id 56320
[  7828.400] (II) RADEON(0): Printing DDC gathered Modelines:
[  7828.401] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
```

---

### Post by shwndzzl on 2011-02-11
> **Krytarik said:**
> *Forlong* meant it more like this ;-):
```
gedit /var/log/Xorg.0.log
```
And please post your "~/.xsession-errors" as well.
```
gedit ~/.xsession-errors
```




gedit ~/.xsession-errors
```
/etc/gdm/Xsession: Beginning session setup...
MainThread 2011/02/11 10:00:31.9280 (sabayon-apply): No profile for user 'shawn' found
No profile for user 'shawn' found
MainThread 2011/02/11 10:00:31.9282 (sabayon-apply): Fatal exception!  Exiting abnormally.
MainThread 2011/02/11 10:00:31.9285 (sabayon-apply): Traceback (most recent call last):
  File "/usr/sbin/sabayon-apply", line 149, in <module>
    sys.exit (util.EXIT_CODE_NO_USER_PROFILE)
SystemExit: 3

===== BEGIN MILESTONES (/usr/sbin/sabayon-apply) =====
MainThread 2011/02/11 10:00:31.9280 (sabayon-apply): No profile for user 'shawn' found
MainThread 2011/02/11 10:00:31.9282 (sabayon-apply): Fatal exception!  Exiting abnormally.
MainThread 2011/02/11 10:00:31.9285 (sabayon-apply): Traceback (most recent call last):
  File "/usr/sbin/sabayon-apply", line 149, in <module>
    sys.exit (util.EXIT_CODE_NO_USER_PROFILE)
SystemExit: 3

===== END MILESTONES (/usr/sbin/sabayon-apply) =====
===== BEGIN RING BUFFER (/usr/sbin/sabayon-apply) =====
MainThread 2011/02/11 10:00:31.9280 (sabayon-apply): No profile for user 'shawn' found
MainThread 2011/02/11 10:00:31.9282 (sabayon-apply): Fatal exception!  Exiting abnormally.
MainThread 2011/02/11 10:00:31.9285 (sabayon-apply): Traceback (most recent call last):
  File "/usr/sbin/sabayon-apply", line 149, in <module>
    sys.exit (util.EXIT_CODE_NO_USER_PROFILE)
SystemExit: 3

===== END RING BUFFER (/usr/sbin/sabayon-apply) =====


This configuration for the debug log can be re-created
by putting the following in ~//etc/sabayon/sabayon-debug-log.conf
(use ';' to separate domain names):

[debug log]
max lines = 1000
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
gnome-session[1729]: EggSMClient-WARNING: Desktop file '/home/shawn/.config/autostart/cairo-dock.desktop' has malformed Icon key 'cairo-dock.svg'(should not include extension)
GNOME_KEYRING_CONTROL=/tmp/keyring-We49pf
SSH_AUTH_SOCK=/tmp/keyring-We49pf/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-We49pf
SSH_AUTH_SOCK=/tmp/keyring-We49pf/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-We49pf
SSH_AUTH_SOCK=/tmp/keyring-We49pf/ssh
gnome-session[1729]: WARNING: Could not launch application 'Screenlets%20Daemon.desktop': Unable to start application: Failed to execute child process "/usr/share/screenlets-manager/screenlets-daemon.py" (No such file or directory)
gnome-session[1729]: WARNING: Could not launch application 'cairo-dock.desktop': Unable to start application: Failed to execute child process "cairo-dock" (No such file or directory)
python: can't open file '/usr/share/screenlets/Output/OutputScreenlet.py': [Errno 2] No such file or directory
gnome-session[1729]: WARNING: Could not launch application '10b3584e0f2b0de97d129649730151353700000016200045.desktop': Unable to start application: Failed to execute child process "evolution-exchange-storage" (No such file or directory)
gnome-session[1729]: WARNING: Could not launch application 'gnome-do.desktop': Unable to start application: Failed to execute child process "gnome-do" (No such file or directory)
gnome-session[1729]: WARNING: Could not launch application 'docky.desktop': Unable to start application: Failed to execute child process "docky" (No such file or directory)
gnome-session[1729]: WARNING: Could not launch application 'mail-notification.desktop': Unable to start application: Failed to execute child process "mail-notification" (No such file or directory)
python: can't open file '/usr/share/screenlets/RingSensors/RingSensorsScreenlet.py': [Errno 2] No such file or directory

(polkit-gnome-authentication-agent-1:1837): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1837): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
Unknown option --sm-config-prefix
** Message: applet now removed from the notification area
** (nm-applet:1838): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1838): DEBUG: foo_client_state_changed_cb
Initializing nautilus-gdu extension
** Message: applet now embedded in the notification area

(nautilus:1817): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** (nm-applet:1838): DEBUG: foo_client_state_changed_cb
gnome-session[1729]: WARNING: Could not launch application '10b3584e0f2b0de97d129649730235855700000016200046.desktop': Unable to start application: Failed to execute child process "/usr/lib/evolution/2.28/evolution-alarm-notify" (No such file or directory)
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2c000b4 (Mozilla Fi)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
** (update-notifier:2261): DEBUG: aptdaemon on bus: 0
** (update-notifier:2261): DEBUG: Skipping reboot required

** (gnome-screensaver:1863): WARNING **: Config key not handled: /desktop/gnome/lockdown/disable_application_handlers

** (gnome-screensaver:1863): WARNING **: Config key not handled: /desktop/gnome/lockdown/disable_command_line

** (gnome-screensaver:1863): WARNING **: Config key not handled: /desktop/gnome/lockdown/disable_printing

** (gnome-screensaver:1863): WARNING **: Config key not handled: /desktop/gnome/lockdown/disable_print_setup

** (gnome-screensaver:1863): WARNING **: Config key not handled: /desktop/gnome/lockdown/disable_save_to_disk
Window manager warning: Received a _NET_WM_MOVERESIZE message for 0x460002f (.Quick Ref); these messages lack timestamps and therefore suck.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x4c00005 (Contact Li)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x4c00005 (Contact Li)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x4c0055f (alec1820@g)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x4c0055f (alec1820@g)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory

(nautilus:1817): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1817): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1817): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1817): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1817): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1817): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1817): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1817): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1817): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1817): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1817): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1817): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1817): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1817): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1817): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1817): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1817): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
```

---

### Post by shwndzzl on 2011-02-11
> **realzippy said:**
> If you run
```
compiz --replace
```compiz only runs as long the as terminal is opened.

```
compiz --replace &
```lets you close the terminal compiz still running;however only for this session.
Again,put it in Startup Applications to get compiz after reboot.


So, I would place this command in a text file and put that file in the start up apps?

---

### Post by realzippy on 2011-02-11
> **shwndzzl said:**
> So, I would place this command in a text file and put that file in the start up apps?

No.In the top panel 
System>Settings>Startup Applications
hit "add"
name: what you want...
command: compiz --replace

---

### Post by Krytarik on 2011-02-11
> **realzippy said:**
> If you run
```
compiz --replace
```compiz only runs as long the as terminal is opened.

```
compiz --replace &
```lets you close the terminal compiz still running;however only for this session.
Again,put it in Startup Applications to get compiz after reboot.
I don't know if that is true for Compiz, but at least for any other apps it isn't, it just brings you to a command prompt after issuing the command, but when you close the terminal, the app also gets killed. Use "setsid" instead, as prefix, like that:
```
setsid compiz --replace
```

---

### Post by Krytarik on 2011-02-11
Your Xorg.0.log looks fine to me, except for the apparent attempt to load the "fglrx" driver.
Check with the following command if any packages of those are installed:
```
dpkg -l|grep fglrx
```
Or did you install it manually one time? If so, did you follow the removal instructions?

As for your .xsession-errors, there are some errors messages in the middle of the log under [debug log]. There seem to be some launchers of apps in "Startup Applications" which have been removed since.

---

### Post by shwndzzl on 2011-02-11
> **realzippy said:**
> No.In the top panel 
System>Settings>Startup Applications
hit "add"
name: what you want...
command: compiz --replace

nice! done and done..

---

### Post by realzippy on 2011-02-15
Does that mean you have tried already and it does not work?
or
it does work?
If so,please mark thread as solved (threadtools)...

---

### Post by shwndzzl on 2011-02-15
> **realzippy said:**
> Does that mean you have tried already and it does not work?
or
it does work?
If so,please mark thread as solved (threadtools)...

Yes, and yes. I will mark it resolved! Thanks everyone!

---

### Post by ElitebookMelodie on 2011-04-13
> **shwndzzl said:**
> Yes, and yes. I will mark it resolved! Thanks everyone!

I just want to confirm if I'm right. So these codes made Compiz Fusion work with firegl v5725?  I saw somewhere else say that the 3D effects don't work since firegl is not 3D capable?  Is that true?

I'm just a bit confused and am a n00b.

---

### Post by realzippy on 2011-04-13
[I]So these codes made Compiz Fusion work with firegl v5725? 
[/I]
???????????
thread was about compiz issues on :
Graphics chip: **ATI** Technologies Inc RS690M [Radeon X1200 Series]

anyway,welcome to the forum!
suggest you google :
name of your graphics card+compiz+ubuntu
If no hits,open an own thread giving all available information of your system and describing your problem and formerly attempts you made
to solve it.

---

