---
title: "(Need help) NVIDIA drivers &gt;177"
date: 2009-04-13
forum: General Help
---

### Post by TheDesertDragon on 2009-04-13
Heya folks!

I've been here once before, and despite the many issues I've had with Ubuntu (most of them being down to my own stupidity) I still prefer it to Windows. I got graphics to work, I got sound to work (God, it was pain. I don't even remember what I did. X-Fi user here) and I have managed to set up my system in such a way that I can never go back to Windows again. :)

Anyway, I'm having trouble again, and this time it's the NVIDIA display drivers (and Wine merging the wheel tilts to the side buttons on the mouse but I'll save that for another time).

Basically, installing any driver version above >177 will cause the X-server to not work and it will need to boot on tty9 in some special safe-mode that disables desktop effects. The error returned is long and confusing, but it's written in English and it basically says, that the driver is just missing. It's just gone.

Installing an older driver says the driver is there, but the X-server won't detect it and the NVIDIA X-server configuration tool is not seeing the driver either. I cannot enable any other drivers through the hardware configuration interface and overall I ... just can't do anything, really. I can downgrade to version and that seems to work, but I have heard of nearly double performance going from 177 to 185 (if not even more than that) so I am rather interested in upgrading.

I am using Ubuntu 8.10 with all the latest updates installed from the update manager. The graphics card is NVIDIA 8800GT 512MB from Inno3D and the mainboard is ASUS P5K (if it's of any relevance)

I am a rather decent Windows programmer, but I am a total nub at Linux, so I'd appreciate responses not being *too* Linux-technical. :)

Thanks for reading and (hopefully) helping.

EDIT: Just tried again using some new instructions. Still no luck. Got this stuff out of the fires:
:0.log
> 5693 5415
xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe with-gdm -- /usr/bin/X :0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7 -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log

X: warning; process set to priority -1 instead of requested priority 0

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux christian-linux 2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686
Build Date: 09 March 2009  10:48:54AM
xorg-server 2:1.5.2-2ubuntu3.1 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Mon Apr 13 17:28:14 2009
(++) Using config file: "/etc/X11/xorg.conf.failsafe"
error setting MTRR (base = 0xf5000000, size = 0x00e00000, type = 1) Invalid argument (22)
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) PreInit returned NULL for "Logitech Logitech RumblePad 2 USB"
(EE) config/hal: NewInputDeviceRequest failed
5693 5415

Xorg.0.log
> 
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux christian-linux 2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686
Build Date: 09 March 2009  10:48:54AM
xorg-server 2:1.5.2-2ubuntu3.1 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 13 17:28:12 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
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
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
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

(--) PCI:*(0@1:0:0) nVidia Corporation GeForce 8800 GT rev 162, Mem @ 0xf6000000/0, 0xd0000000/0, 0xf4000000/0, I/O @ 0x0000cc00/0, BIOS @ 0x????????/131072
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
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
(II) LoadModule: "type1"

(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  185.19  Fri Apr  3 12:55:43 PST 2009
(II) Loading extension GLX
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
(II) LoadModule: "kbd"

(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) LoadModule: "mouse"

(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) NVIDIA dlloader X Driver  185.19  Fri Apr  3 12:30:48 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
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
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) NVIDIA(0):     system's kernel log for additional error messages and
(EE) NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

---

### Post by sdennie on 2009-04-13
Ubuntu does some odd things with the nvidia driver and if you try to install an external driver, it won't work unless you uninstall what Ubuntu is using.  There are many guides available for doing this.  It's very easy to do this.  Google will give you more but, this one looks good: [http://ubuntuforums.org/showpost.php?p=5086971](http://ubuntuforums.org/showpost.php?p=5086971)

---

### Post by TheDesertDragon on 2009-04-13
I see. I'll try that. Thanks! :)

EDIT: It didn't work. It looks exactly the same as before.

Well, it's worse. Before I just had low graphics settings. Now I have low graphics settings with the upper 1/10 of the screen displaying random colors and a screen cut over at about 2/5th's in. (Moving the cursor to the end of the screen makes it appear on the other side, and the mouse stops at the middle of the screen from both sides. Bad screen wrap)

Consider it a wonder I could even reach the Firefox icon! xD

EDIT2: Going into the System -> Administration -> Hardware Drivers menu still reveals 3 drivers, even after using 

sudo apt-get remove --purge nvidia*
sudo rm /lib/restricted-modules/.nvidia* (<--- Actually, I already did this beforehand with the Synaptics package handler)

EDIT3: (God, this is getting old) However, going in there while the desktop is bugged reveals that there are no propriety drivers present on the system.

Wut?

---

### Post by TheDesertDragon on 2009-04-13
Bump

---

### Post by sdennie on 2009-04-13
Based on your log, the problem is still exactly what I'm describing.  You've either not built the drivers correctly or you've built them and they are being overridden by Ubuntu default drivers.

---

### Post by TheDesertDragon on 2009-04-13
> **sdennie said:**
> Based on your log, the problem is still exactly what I'm describing.  You've either not built the drivers correctly or you've built them and they are being overridden by Ubuntu default drivers.

Your explanation sounds absolutely reasonable and plausable. It just still won't work... :/ I'm going to try downloading the 180.44 and try those instead of 185.19 but I doubt it'll be any different.

---

### Post by sdennie on 2009-04-13
The driver version won't make any difference.  Once you've got your machine sanitized to accept external drivers, you can install whatever you want.  But, the proper installation after the sanitation is key.  (Although, I do recommend the new 185 driver.  It's great.)

---

### Post by TheDesertDragon on 2009-04-13
That's the thing. I installed an external 177.84 driver without issues but I cannot install 180.44 (which used to show up on the list) and I cannot install 185.19.

All this applies before and after the fix described above.

I appreciate your help, but I think the issue is elsewhere.

Oh, and I just installed 177 again and it works flawlessly, as always, although it is extremely slow and Gnome's title bars may sometimes bug out while running Compiz (they freeze) This is because it's a beta driver. And by extremely slow I mean slightly slower than Windows! :P

---

### Post by sdennie on 2009-04-13
Ok.  That is indeed an odd problem.  Do the newer drivers install correctly?

---

### Post by TheDesertDragon on 2009-04-13
> **sdennie said:**
> Ok.  That is indeed an odd problem.  Do the newer drivers install correctly?

Absolutely flawlessly. And if I run the installer again it will even tell me that driver version 185.19 is already installed and asks if I would like to remove it first.

The x-server, however, cannot find it. The NVIDIA x-server config tool cannot find it either.

PS: I am playing WoW on 177.86 atm. :) (And getting 100 FPS in Orgrimmar on Stormscale EU. Twice what I get one Windows... Ohwell) But I am still here also.

---

### Post by sdennie on 2009-04-13
Strange.  What kernel are you running.  Normal Ubuntu kernel or custom compiled?

---

### Post by TheDesertDragon on 2009-04-13
I downloaded Ubuntu (the standard version) from the Ubuntu site in the start of 2008 and installed it with the installation tool on the CD which I burned it to. As far as I know I didn't compile anything. I am not using Kubuntu og Xubuntu etc. etc. either. I am running 8.10 32-bit. (But I have >4GB RAM! :/ Should upgrade but cba! D: ) So I guess the answer must be:

Normal Ubuntu kernel.

---

### Post by jocheem67 on 2009-04-13
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

Here's another link that you might try, it's even a bit less complex than the former one. It has never failed me.

---

### Post by sdennie on 2009-04-13
His card is not only supported by the new drivers but, the newer drivers are actually aimed at performance for his card.  That's why I find this all very strange.  Based on the logs, it's like the newer kernel module isn't being built when he installs the newer drivers.

Edit:
As for the memory issue, see: [ Ubuntu with 4GB+ of memory]("http://ubuntuforums.org/showthread.php?t=855511")

---

### Post by TheDesertDragon on 2009-04-13
> **jocheem67 said:**
> [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

Here's another link that you might try, it's even a bit less complex than the former one. It has never failed me.

That tutorial simply described what I've been doing all along. It's the standard install procedure. Remove old driver, restart system, shut down X-server, install driver, restart.

That's where the error comes in.

---

### Post by ibuclaw on 2009-04-13
Try starting X with the non-working NVIDIA drivers again.
When it fails, switch to a tty and stop gdm:
```

sudo /etc/init.d/gdm stop

sudo killall Xorg

```

Now collect all required data to fully debug your problem:
```

grep "^(EE)" /var/log/Xorg.0.log >~/Desktop/Xorg.log

grep -i "nvidia\|NVRM" /var/log/syslog.0 >~/Desktop/syslog.log

dpkg -l nvidia* >~/Desktop/dpkglist.log

cat /etc/X11/xorg.conf >~/Desktop/xorg.conf

```

And restore X and bring back up gdm
```
sudo dpkg-reconfigure -phigh xserver-xorg

sudo /etc/init.d/gdm start

```
**Note:** If you are using another method to restore X back, use that way instead.


Now, log into the forums and post the contents of each of the files you created. :)

Regards
Iain

---

### Post by TheDesertDragon on 2009-04-13
> **tinivole said:**
> Try starting X with the non-working NVIDIA drivers again.
When it fails, switch to a tty and stop gdm:
```

sudo /etc/init.d/gdm stop

sudo killall Xorg

```

Now collect all required data to fully debug your problem:
```

**grep "^(EE)" /var/log/Xorg.0.log" >~/Desktop/Xorg.log**

grep -i "nvidia\|NVRM" /var/log/syslog.0 >~/Desktop/syslog.log

dpkg -l nvidia* >~/Desktop/dpkglist.log

cat /etc/X11/xorg.conf >~/Desktop/xorg.conf

```

And restore X and bring back up gdm
```
sudo dpkg-reconfigure -phigh xserver-xorg

sudo /etc/init.d/gdm start

```
**Note:** If you are using another method to restore X back, use that way instead.


Now, log into the forums and post the contents of each of the files you created. :)

Regards
Iain

I'm sorry but I can't do this. As soon as I get to the bolded step my user@user~linux: commandline turns into just >

From there, any command I enter is not interpreted but simply saved, so that I can later press arrow-up and type in many commands at once.

In this state however, I can't even restart the x-server. I had to go another terminal to do that.

Nub-alert. I can't do it. What am I doing wrong?

Also, I was using that way to start up Gnome. :P

EDIT2:
Nvm, got it to work. You've written one " too many in the line and I have to type >~/Skrivebord instead as I am using a Danish version of Ubuntu. Might want to mention that... :/

---

### Post by TheDesertDragon on 2009-04-13
The logs:
dpkglist.log:
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Navn                                       Version                                              Beskrivelse
+++-==========================================-====================================================-============================================
un  nvidia-173-kernel-source                   <ingen>                                              (ingen tilgængelig beskrivelse)
pn  nvidia-173-modaliases                      <ingen>                                              (ingen tilgængelig beskrivelse)
pn  nvidia-177-kernel-source                   <ingen>                                              (ingen tilgængelig beskrivelse)
pn  nvidia-177-modaliases                      <ingen>                                              (ingen tilgængelig beskrivelse)
pn  nvidia-180-kernel-source                   <ingen>                                              (ingen tilgængelig beskrivelse)
pn  nvidia-180-libvdpau                        <ingen>                                              (ingen tilgængelig beskrivelse)
pn  nvidia-180-modaliases                      <ingen>                                              (ingen tilgængelig beskrivelse)
un  nvidia-71-kernel-source                    <ingen>                                              (ingen tilgængelig beskrivelse)
pn  nvidia-71-modaliases                       <ingen>                                              (ingen tilgængelig beskrivelse)
un  nvidia-96-kernel-source                    <ingen>                                              (ingen tilgængelig beskrivelse)
pn  nvidia-96-modaliases                       <ingen>                                              (ingen tilgængelig beskrivelse)
pn  nvidia-common                              <ingen>                                              (ingen tilgængelig beskrivelse)
un  nvidia-glx                                 <ingen>                                              (ingen tilgængelig beskrivelse)
un  nvidia-glx-173                             <ingen>                                              (ingen tilgængelig beskrivelse)
ic  nvidia-glx-177                             177.82-0ubuntu0.1                                    NVIDIA binary Xorg driver
ic  nvidia-glx-180                             180.37-0ubuntu2                                      NVIDIA binary Xorg driver
un  nvidia-glx-71                              <ingen>                                              (ingen tilgængelig beskrivelse)
un  nvidia-glx-96                              <ingen>                                              (ingen tilgængelig beskrivelse)
un  nvidia-glx-envy                            <ingen>                                              (ingen tilgængelig beskrivelse)
un  nvidia-glx-legacy                          <ingen>                                              (ingen tilgængelig beskrivelse)
un  nvidia-glx-legacy-envy                     <ingen>                                              (ingen tilgængelig beskrivelse)
rc  nvidia-glx-new                             169.12+2.6.24.16-23.56                               NVIDIA binary XFree86 4.x/X.Org 'new' driver
un  nvidia-glx-new-envy                        <ingen>                                              (ingen tilgængelig beskrivelse)
un  nvidia-glx-src                             <ingen>                                              (ingen tilgængelig beskrivelse)
un  nvidia-kernel-169.12                       <ingen>                                              (ingen tilgængelig beskrivelse)
un  nvidia-kernel-71.86.04                     <ingen>                                              (ingen tilgængelig beskrivelse)
un  nvidia-kernel-96.43.05                     <ingen>                                              (ingen tilgængelig beskrivelse)
pn  nvidia-kernel-common                       <ingen>                                              (ingen tilgængelig beskrivelse)
un  nvidia-kernel-source                       <ingen>                                              (ingen tilgængelig beskrivelse)
un  nvidia-kernel-source-envy                  <ingen>                                              (ingen tilgængelig beskrivelse)
un  nvidia-kernel-src                          <ingen>                                              (ingen tilgængelig beskrivelse)
un  nvidia-legacy-kernel-source                <ingen>                                              (ingen tilgængelig beskrivelse)
un  nvidia-legacy-kernel-source-envy           <ingen>                                              (ingen tilgængelig beskrivelse)
un  nvidia-new-kernel-source                   <ingen>                                              (ingen tilgængelig beskrivelse)
un  nvidia-new-kernel-source-envy              <ingen>                                              (ingen tilgængelig beskrivelse)
pn  nvidia-settings                            <ingen>                                              (ingen tilgængelig beskrivelse)
un  nvidia-xconfig                             <ingen>                                              (ingen tilgængelig beskrivelse)
```syslog.log
```
Apr 12 23:19:18 christian-linux kernel: [   12.971375] nvidia: module license 'NVIDIA' taints kernel.
Apr 12 23:19:18 christian-linux kernel: [   13.284507] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 12 23:19:18 christian-linux kernel: [   13.284514] nvidia 0000:01:00.0: setting latency timer to 64
Apr 12 23:19:18 christian-linux kernel: [   13.296496] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.17  Sun Dec 14 20:25:46 PST 2008
```Xorg.log
```
(EE) Failed to load module "type1" (module does not exist, 0)
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) NVIDIA(0):     system's kernel log for additional error messages and
(EE) NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.
```xorg.conf
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Fri Apr  3 13:01:52 PST 2009


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
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

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```The funny thing here is... After doing this error report, I started it up and the error DID NOT OCCUR. However, the screen flashes black whenever Compiz tries to use an advanced effect, and 3D programs cannot find a suitable device.

Btw: Ingen means nothing and ingen tilgængelig beskrivelse means no description available.

EDIT: Ahh...
sudo dpkg-reconfigure -phigh xserver-xorg
turns off the graphics driver, doesn't it? :)

---

### Post by ibuclaw on 2009-04-13
Well, all what I can see wrong initially is just one erroneous line in the xorg.conf file.

```
sudo nano /etc/X11/xorg.conf
```
And remove this line in bold:
```

Section "Module"
    Load           "dbe"
    Load           "extmod"
**    Load           "type1"**
    Load           "freetype"
    Load           "glx"
EndSection

```

Also, you seem to have some residual configuration of an uninstalled package (nvidia-glx-new). Though, it is hard to tell whether or not this is playing a part in the load sequence.

And yes, 'dpkg-reconfigure -phigh xserver-xorg' resets the graphics configuration back to the default Vesa drivers.

Regards
Iain

---

### Post by TheDesertDragon on 2009-04-13
In Windows right now. (One of my friends wanted to play arena. It's not going to well. We just fell below 2k! :( )

I'll try that one later. I'll reinstall the driver and go to that file and change that exact line and reboot, and I'll say here what happens. (I could also post new logs)

---

### Post by TheDesertDragon on 2009-04-13
> **tinivole said:**
> Well, all what I can see wrong initially is just one erroneous line in the xorg.conf file.

```
sudo nano /etc/X11/xorg.conf
```
And remove this line in bold:
```

Section "Module"
    Load           "dbe"
    Load           "extmod"
**    Load           "type1"**
    Load           "freetype"
    Load           "glx"
EndSection

```

Also, you seem to have some residual configuration of an uninstalled package (nvidia-glx-new). Though, it is hard to tell whether or not this is playing a part in the load sequence.

And yes, 'dpkg-reconfigure -phigh xserver-xorg' resets the graphics configuration back to the default Vesa drivers.

Regards
Iain

I'm afraid this didn't work either. I deleted the line in the file as you specified, and nothing changed. I get the same error in the same way.

I'm going to keep a close eye on this thread, as it has been surprisingly productive for me. Even though it hasn't resolved the issue, it's taught my a lot about Linux. And you people... are awesome! <3

---

### Post by TheDesertDragon on 2009-04-14
/bump

Still need help! :(

---

### Post by ibuclaw on 2009-04-14
Actually, I forgot to ask, are you installing the drivers manually?
As in, downloading them from their site rather than through **Hardware Drivers** in Ubuntu?

Again, I'll ask you to review your Xorg and syslog for a reason as to why it is still failing now.

```

grep "^(EE)" /var/log/Xorg.0.log >~/Desktop/Xorg.log

grep -i "nvidia\|NVRM" /var/log/syslog.0 >~/Desktop/syslog.log

```
**Note:** sorry about the extra " last time, it isn't there now. ;)

Regards
Iain

---

### Post by TheDesertDragon on 2009-04-14
I install drivers manually. I switch to terminal one, close down gdm, install the driver through the file directly, so I get guided through the setup proceedure by NVIDIA's installer, and then I restart the PC, and the error occurs.

I'll be popping back with logs in a minute! :)

EDIT: I used the dpkg-reconfigure command before starting the X-server after crashing it and writing the logs. If that's wrong, please tell me.

Syslog.log:
```
Apr 12 23:19:18 christian-linux kernel: [   12.971375] nvidia: module license 'NVIDIA' taints kernel.
Apr 12 23:19:18 christian-linux kernel: [   13.284507] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 12 23:19:18 christian-linux kernel: [   13.284514] nvidia 0000:01:00.0: setting latency timer to 64
Apr 12 23:19:18 christian-linux kernel: [   13.296496] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.17  Sun Dec 14 20:25:46 PST 2008
```
Xorg.log:
```
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) NVIDIA(0):     system's kernel log for additional error messages and
(EE) NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.
```

---

### Post by TheDesertDragon on 2009-04-14
Just looked a bit through the NVIDIA readme file.

It says:

> Q. My X server fails to start, and my X log file contains the error:
   
   (EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
   
   
A. The X driver will abort with this error message if the NVIDIA kernel module
   fails to load. If you receive this error, you should check the output of
   `dmesg` for kernel error messages and/or attempt to load the kernel module
   explicitly with `modprobe nvidia`. If unresolved symbols are reported, then
   the kernel module was most likely built against a Linux kernel source tree
   (or kernel headers) for a kernel revision or configuration that doesn't
   match the running kernel.

   You can specify the location of the kernel source tree (or headers) when
   you install the NVIDIA driver using the --kernel-source-path command line
   option (see `sh NVIDIA-Linux-x86-185.19-pkg1.run --advanced-options` for
   details).

   Old versions of the module-init-tools include `modprobe` binaries that
   report an error when instructed to load a module that's already loaded into
   the kernel. Please upgrade your module-init-tools if you receive an error
   message to this effect.

   The X server reads '/proc/sys/kernel/modprobe' to determine the path to the
   `modprobe` utility and falls back to '/sbin/modprobe' if the file doesn't
   exist. Please make sure that this path is valid and refers to a `modprobe`
   binary compatible with the Linux kernel running on your system.

   The "LoadKernelModule" X driver option can be used to change the default
   behavior and disable kernel module auto-loading.


So I went into /proc/sys/kernel/modprobe and found the file empty.

Is this the problem? :P

---

### Post by TheDesertDragon on 2009-04-14
/bump

D:

---

### Post by ibuclaw on 2009-04-14
Upon hearing that you manually installed the drivers, I would initially advise you to uninstall/purge all nvidia packages from the Ubuntu repository then, as from your dpkg -l output, there are still some traces that exist, and may be conflicting wildly.

```
sudo aptitude purge $(dpkg -l | grep nvidia | awk '{print $2}')
```
This may require reinstallation of your manually installed driver (only time will tell).

Although, if its of any concern to you, I am actually in the middle of writing up a HowTo on installing the NViDIA 185.19 beta drivers. If interested, you may redirect all help to there once I've finished it.

Regards
Iain

---

### Post by TheDesertDragon on 2009-04-14
> **tinivole said:**
> Upon hearing that you manually installed the drivers, I would initially advise you to uninstall/purge all nvidia packages from the Ubuntu repository then, as from your dpkg -l output, there are still some traces that exist, and may be conflicting wildly.

```
sudo aptitude purge $(dpkg -l | grep nvidia | awk '{print $2}')
```
This may require reinstallation of your manually installed driver (only time will tell).

Although, if its of any concern to you, I am actually in the middle of writing up a HowTo on installing the NViDIA 185.19 beta drivers. If interested, you may redirect all help to there once I've finished it.

Regards
Iain

Wowowowowow... Hold on just a minute right there! =P

While it did find the 2 NVIDIA-packages it mentioned, it wanted to uninstall 270MB worth of data, including java, gnome, python libraries and god knows what other stuff. My screen was littered full of items. D:

I said no, in fear of ****ing up the system for good. Should I be concerned with the long list or just go ahead?

EDIT:
The list:
```
  binutils-static{u} bsh{u} dkms{u} gcj-4.2-base{u} gcj-4.3-base{u}
  gij{u} gij-4.2{u} gij-4.3{u} kdelibs-data{u} kdelibs4c2a{u}
  libarts1c2a{u} libartsc0{u} libavahi-qt3-1{u} libgcj-bc{u}
  libgcj8-1{u} libgcj9-0{u} libgcj9-0-awt{u} libgcj9-jar{u}
  libhsqldb-java{u} libjaxp1.3-java{u} libjline-java{u} liblua50{u}
  liblualib50{u} libpythonize0{u} libqt3-mt{u}
  libservlet2.4-java{u} libxalan2-java{u} libxerces2-java{u}
  nvidia-glx-177{p} nvidia-glx-180{p} nvidia-glx-new{p}
  openoffice.org-filter-binfilter{u} pykdeextensions{u}
  python-kde3{u} python-qt3{u} python-sip4{u} xaw3dg{u}
```

---

### Post by ibuclaw on 2009-04-14
> **TheDesertDragon said:**
> 
EDIT:
The list:
```
  binutils-static{u} bsh{u} dkms{u} gcj-4.2-base{u} gcj-4.3-base{u}
  gij{u} gij-4.2{u} gij-4.3{u} kdelibs-data{u} kdelibs4c2a{u}
  libarts1c2a{u} libartsc0{u} libavahi-qt3-1{u} libgcj-bc{u}
  libgcj8-1{u} libgcj9-0{u} libgcj9-0-awt{u} libgcj9-jar{u}
  libhsqldb-java{u} libjaxp1.3-java{u} libjline-java{u} liblua50{u}
  liblualib50{u} libpythonize0{u} libqt3-mt{u}
  libservlet2.4-java{u} libxalan2-java{u} libxerces2-java{u}
  nvidia-glx-177{p} nvidia-glx-180{p} nvidia-glx-new{p}
  openoffice.org-filter-binfilter{u} pykdeextensions{u}
  python-kde3{u} python-qt3{u} python-sip4{u} xaw3dg{u}
```
:O

OK!
```
sudo aptitude install dkms binutils-static
```
Those are the two most important packages there. The rest look to be from a KDE application you recently uninstalled ???

Also, if in doubt, it may be best to use apt-get instead.
```
sudo apt-get --purge remove $(dpkg -l | grep nvidia | awk '{print $2}')
```

Regards
Iain

---

### Post by TheDesertDragon on 2009-04-14
Oh nonono! :P I did abort the installation before doing that! =P I kindda got the sense that... yeah... something wasn't right! xD

I'll try the new command.

EDIT:

Wtf at this retarded OS sometimes. I love it and hate it at the same time! D: Bad for my sanity! :P

Først command gave:

Indlæser pakkelisterne... Færdig                                       
Opbygger afhængighedstræ                                               
Læser tilstandsoplysninger... Færdig                                   
Læser oplysninger om udvidet status                                    
klargører pakketilstande... Færdig                                     
Følgende pakker vil blive AFINSTALLERET:      (EDIT: Means removed)                         
  bsh{u} gcj-4.2-base{u} gcj-4.3-base{u} gij{u} gij-4.2{u}             
  gij-4.3{u} kdelibs-data{u} kdelibs4c2a{u} libarts1c2a{u}             
  libartsc0{u} libavahi-qt3-1{u} libgcj-bc{u} libgcj8-1{u}             
  libgcj9-0{u} libgcj9-0-awt{u} libgcj9-jar{u} libhsqldb-java{u}       
  libjaxp1.3-java{u} libjline-java{u} liblua50{u} liblualib50{u}       
  libpythonize0{u} libqt3-mt{u} libservlet2.4-java{u}                  
  libxalan2-java{u} libxerces2-java{u}                                 
  openoffice.org-filter-binfilter{u} pykdeextensions{u}
  python-kde3{u} python-qt3{u} python-sip4{u} xaw3dg{u}
0 pakker opgraderet, 0 nyinstalleret, 32 til afinstallering og 0 ikke opgraderet.
Skal hente 0B arkiver. Efter udpakning vil 258MB blive frigjort.
Vil du fortsætte) [Y/n?] n
Afbryd.

The second command turned up with:
Indlæser pakkelisterne... Færdig
Opbygger afhængighedstræ
Læser tilstandsoplysninger... Færdig
Pakken nvidia-glx-177 er ikke installeret, så den afinstalleres ikke             <--- /sigh
Pakken nvidia-glx-180 er ikke installeret, så den afinstalleres ikke             <--- /sigh 
Pakken nvidia-glx-new er ikke installeret, så den afinstalleres ikke             <--- /sigh
Følgende pakker blev installeret automatisk, og behøves ikke længere:
  gcj-4.3-base libarts1c2a kdelibs4c2a libartsc0 libgcj8-1 libgcj9-0
  libgcj-bc libpythonize0 openoffice.org-filter-binfilter kdelibs-data
  liblualib50 libservlet2.4-java binutils-static pykdeextensions
  gij-4.2 gij-4.3 python-qt3 bsh gcj-4.2-base libavahi-qt3-1 gij
  python-sip4 libjaxp1.3-java dkms libjline-java libgcj9-jar
  libxerces2-java libxalan2-java libgcj9-0-awt libhsqldb-java xaw3dg
  libqt3-mt liblua50 python-kde3
Brug 'apt-get autoremove' til at fjerne dem.
0 opgraderes, 0 nyinstalleres, 0 afinstalleres og 0 opgraderes ikke.

In other words, it says "doesn't exist, won't remove."

All the libraries mentioned above are said to be unneccasary.

EDIT: Did it after talking to my friends. I removed all those libraries and ran the first command you supplied. Apparently a lot of libraries needed to be updated. Worth trying to install the drivers again?
EDIT2: Using yours first command, it now only supplied the 3 NVIDIA leftovers and removed them correctly. :)

---

### Post by ibuclaw on 2009-04-14
Also,
```
sudo apt-get install linux-restricted-modules-generic
```

That is the only plausible reason I can think as to why binutils-static and dkms are up for pending removal.

[EDIT]
hmm... If you genuinely don't want anything removed. Then just type in
```
aptitude
```
and you'll be shown a curses application.

Press **g** and you'll be showing a pending updates page. Scroll up to the "**Packages to be Removed**" title bar, then press the **+** button to remark all pending removal items as manually installed, and press **g** again to switch to root. (You may need to press **+** again to mark all as manually installed) then press **g** to confirm and aptitude will run the request (and do nothing), then return.

Press **q** several times to quit aptitude, then:
```
sudo aptitude purge $(dpkg -l | grep nvidia | awk '{print $2}')
```
as that will **definately** remove the packages. (Not sure why apt-get wont ???)

Regards
Iain

---

### Post by TheDesertDragon on 2009-04-14
I don't know why either, but I got it resolved now.

The driver, however, still doesn't work. I just tried installing it again and it did exactly the same. Installed beautifully, but gave a bunch of warnings about modifications to the driver and some missing old driver files during uninstallation. (that one is rather obvious seeing what we just did)

However, the driver still fails to work. D:
I've asked my friend about what he did (he just got it up and running on a fresh Linux installation). Hoping for a reply soon. In the meantime, I'm looking forward to your guide! :)

EDIT: He had major headaches before a reinstallation of Linux. After reinstalling, the new drivers installed without a hitch...

I guess there's only one thing left to do... >_>

---

### Post by ibuclaw on 2009-04-14
Here is my guide:
[http://ubuntuforums.org/showthread.php?p=7070589#post7070589](http://ubuntuforums.org/showthread.php?p=7070589#post7070589)

Also, considering your predicament. Try running the nvidia-uninstaller, reload up the default failsafe drivers, and again double check that nothing nvidia-related is installed through apt/dpkg.

```
sudo nvidia-uninstall
sudo dpkg-reconfigure -phigh xserver-xorg
sudo aptitude purge $(dpkg -l | grep nvidia | awk '{print $2}'
```

Then follow through the guide, and hopefully all shall work out. (I've just tested it against one of my machines, and I had no issues whatsoever ... so I hope the same for you).

Regards
Iain

---

### Post by TheDesertDragon on 2009-04-20
Still got problems with this.

Just tried the new 180.51 (people had claimed it worked) and it didn't. Getting completely burned out on this. 

This is the sort of stuff that just keeps scaring me away from Linux. I love this OS but nothing just works on it. Programs are unstable or crash all the time and drivers aren't even tested against the newest version of it. This is obv. due to the large amounts of distros and stuff like that but it's still extremely annoying... And don't even talk to me about my soundcard. Gah! I had to buy a second one which, as chance would have it, doesn't work on Windows. So now I need to switch back and forth whenever I change OS!

/rant
/sigh

I got the usual, pretty much. Anybody got some good suggestions?

Xorg.0.log:
```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux christian-linux 2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686
Build Date: 09 March 2009  10:48:54AM
xorg-server 2:1.5.2-2ubuntu3.1 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 20 17:58:00 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
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
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
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

(--) PCI:*(0@1:0:0) nVidia Corporation GeForce 8800 GT rev 162, Mem @ 0xf6000000/0, 0xd0000000/0, 0xf4000000/0, I/O @ 0x0000cc00/0, BIOS @ 0x????????/131072
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
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
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.51  Thu Apr 16 19:32:09 PDT 2009
(II) Loading extension GLX
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
(II) LoadModule: "kbd"

(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) LoadModule: "mouse"

(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) NVIDIA dlloader X Driver  180.51  Thu Apr 16 19:08:39 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
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
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

:0.log
```
7533 7392
xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe with-gdm -- /usr/bin/X :0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7 -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log

X: warning; process set to priority -1 instead of requested priority 0

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux christian-linux 2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686
Build Date: 09 March 2009  10:48:54AM
xorg-server 2:1.5.2-2ubuntu3.1 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Mon Apr 20 17:58:02 2009
(++) Using config file: "/etc/X11/xorg.conf.failsafe"
error setting MTRR (base = 0xf5000000, size = 0x00e00000, type = 1) Invalid argument (22)
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) PreInit returned NULL for "Logitech Logitech RumblePad 2 USB"
(EE) config/hal: NewInputDeviceRequest failed
7533 7392
tar: Removing leading `/' from member names
```

EDIT: I'll be going back to the LTS tomorrow. I love the new version a lot but all this fuss... it's just not worth it. Those driver kinks really need to be worked out first! :(

---

### Post by ibuclaw on 2009-04-20
I think the /var/log/syslog file is crucial here. You should really be reviewing that as well, as more info/warning/error messages get posted there too.

Although, just for clarifications sake, are you sure that there is only one nvidia kernel module and/or xorg drivers present?
```

find /usr/lib/xorg/modules -name "*glx*" | xargs ls -l
find /usr/lib/xorg/modules -name "*nvidia*" | xargs ls -l
find /lib/modules -type f -name "*nvidia*" | xargs ls -l

```

And post everything that tells you.

Regards
Iain

---

### Post by TheDesertDragon on 2009-04-23
```
christian@christian-linux:~$ find /usr/lib/xorg/modules -name "*glx*" | xargs ls -l
lrwxrwxrwx 1 root root      16 2009-04-21 01:07 /usr/lib/xorg/modules/extensions/libglx.so -> libglx.so.177.82
-rwxr-xr-x 1 root root 1246936 2009-04-21 01:07 /usr/lib/xorg/modules/extensions/libglx.so.177.82
christian@christian-linux:~$ find /usr/lib/xorg/modules -name "*nvidia*" | xargs ls -l
-rwxr-xr-x 1 root root 4998900 2009-04-21 01:07 /usr/lib/xorg/modules/drivers/nvidia_drv.so
lrwxrwxrwx 1 root root      23 2009-04-21 01:07 /usr/lib/xorg/modules/libnvidia-wfb.so.1 -> libnvidia-wfb.so.177.82
-rwxr-xr-x 1 root root  270552 2009-04-21 01:07 /usr/lib/xorg/modules/libnvidia-wfb.so.177.82
christian@christian-linux:~$ find /lib/modules -type f -name "*nvidia*" | xargs ls -l
-rw-r--r-- 1 root root   12648 2009-01-26 05:31 /lib/modules/2.6.24-23-generic/kernel/drivers/char/agp/nvidia-agp.ko
-rw-r--r-- 1 root root   57024 2009-01-26 05:31 /lib/modules/2.6.24-23-generic/kernel/drivers/video/nvidia/nvidiafb.ko
-rw-r--r-- 1 root root 6096247 2009-03-25 19:02 /lib/modules/2.6.24-23-generic/kernel/drivers/video/nvidia/nvidia.ko
-rw-r--r-- 1 root root   20204 2009-04-02 00:46 /lib/modules/2.6.27-11-generic/kernel/drivers/char/agp/nvidia-agp.ko
-rw-r--r-- 1 root root   13124 2009-04-02 00:47 /lib/modules/2.6.27-11-generic/kernel/drivers/video/backlight/mbp_nvidia_bl.ko
-rw-r--r-- 1 root root 7613167 2009-04-21 01:07 /lib/modules/2.6.27-11-generic/kernel/drivers/video/nvidia.ko
-rw-r--r-- 1 root root   66256 2009-04-02 00:47 /lib/modules/2.6.27-11-generic/kernel/drivers/video/nvidia/nvidiafb.ko

```

This is what I got. This is with the 177.82 drivers though. I'm currently upgrading to 9.04 to see if it works any better. As soon as I'm done I'm going to remove all my drivers (hopefully) and try 180.51. (It has a quick patch in it that allows it to compile on the new kernel)

---

### Post by TheDesertDragon on 2009-04-23
Just bumped as reply to tinivole and the others. A big THANK you for all the support you gave me, and I am happy to announce that, while your help was very much appreciated, it did not fix the problem. Ubuntu 9.04, "Jaunty Jackalope", however, did!

It reported a bunch of warnings at one point during the upgrade and started repairing it. I restarted the PC after upgrading, and logged back on. I obviously got an error, since my drivers were not correctly configured for the new kernel. So I removed and purged my drivers and installed 180.51. It installed and ran flawlessly.

I am currently running with 180.51, and it is awesome.

Much love! =D> \\:D/

Sincerely
 - TheDesertDragon

---

