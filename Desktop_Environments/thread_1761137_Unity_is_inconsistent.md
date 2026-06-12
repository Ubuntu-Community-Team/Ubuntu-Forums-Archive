---
title: "Unity is inconsistent"
date: 2011-05-17
forum: Desktop Environments
---

### Post by geovino on 2011-05-17
I've been using 11.04 for two weeks now and sometimes Unity w/sidebar shows up and sometimes it boots up to Classic mode. What's up with that? Why can't Ubuntu make up its mind? Also the boot up is the slowest I've seen since the five years of using Ubuntu. 

Does anyone else have these problems? Can it be fixed? Or do I wait until October when 11.10 comes out?  Does the 32bit version work better?


I'm running 11.04 64bit on a Acer Extensa 4420 w/3GB RAM

---

### Post by Krytarik on 2011-05-17
To force Unity to allways run, you can add "UNITY_FORCE_START=1" to "/etc/environment".

But no quick shot about the slow startup process. You may take a look into the log files "/var/log/messages" and "/var/log/Xorg.0.log", depending on what is the slow part.

Greetings.

---

### Post by geovino on 2011-05-17
> **Krytarik said:**
> To force Unity to allways run, you can add "UNITY_FORCE_START=1" to "/etc/environment".

But no quick shot about the slow startup process. You may take a look into the log files "/var/log/messages" and "/var/log/Xorg.0.log", depending on what is the slow part.

Greetings.

I have not etc/environment directory. 
And now compiz is not working.... :(

I'll reinstall 11.04 or install Mint 11 when it comes out. Mint seems to refine Ubuntu and makes it better. :)

---

### Post by NormanFLinux on 2011-05-17
Install Unity 2D even if you have accelerated graphics.

Send Canonical a message: you want Unity without the bloat.

---

### Post by Krytarik on 2011-05-17
> **geovino said:**
> I have not etc/environment directory.
It's a file, and it's definitely there. Of course you need root access to edit it.
> **geovino said:**
> And now compiz is not working....
What exactly does that mean?

---

### Post by geovino on 2011-05-17
> **Krytarik said:**
> It's a file, and it's definitely there. Of course you need root access to edit it.

What exactly does that mean?it doesn't work.

I'm reinstalling Ubuntu 11.04. I'll let you how it goes...

---

### Post by geovino on 2011-05-17
just installed 11.04 again...

nvidia is not recognized. so no compiz or Unity panel, but it came up one time and after three more boot ups its gone... very inconsistent. 

How do you get nvidia to install drivers? It normally finds it itself. Every other version has done a better job than this one. It's disappointing. I hope 11.10 is better than this!

---

### Post by wildmanne39 on 2011-05-18
> **geovino said:**
> just installed 11.04 again...

nvidia is not recognized. so no compiz or Unity panel, but it came up one time and after three more boot ups its gone... very inconsistent. 

How do you get nvidia to install drivers? It normally finds it itself. Every other version has done a better job than this one. It's disappointing. I hope 11.10 is better than this!

Hi, you do like always go into additional drivers as called restricted at one time, then click on it and see if your driver for your card is there? it should be sense you are running nvidia, one of them will work better for your card then the other one will, but you will have to figure that out, and it may show active but not in use after you activate it and restart the system, but it really is using it.):P

---

### Post by geovino on 2011-05-18
For some reason it didn't find the nvidia drivers. It did ten days ago. I installed the 173 nvidia which has worked before but this time afer reboot it didn't give me the 3D desktop effects. I don't know why. I've installed many versions of Ubuntu over the past five years and this has been the most trouble. And this is the third version of Ubuntu I've installed on this Acer laptop.

... may wipe the hard drive clean with parted magic and start all over again to see if the install will notice that it needs nvidia and the broadcom wifi drivers which do show up.

---

### Post by HugoSerrano on 2011-05-18
You can always try to install Nvidia drivers from Nvidia website.

[http://www.nvidia.com/Download/index.aspx?lang=en-uk](http://www.nvidia.com/Download/index.aspx?lang=en-uk)


After you install them, if it fails to start, do:
#mv /etc/X11/xorg.conf /etc/X11/xorg.conf_notworking
#reboot


Regards!

---

### Post by geovino on 2011-05-18
Well I started over... wiped the hard drive with parted magic and this time when I ran the live CD I clicked Try instead of Install so it booted up as a Live CD, and this time it recognized the nvidia card and the Unity side panel. So I ran the install and after it finished it rebooted to the Unity Desktop! Like is was supposed to. I installed the wifi card and rebooted again and set up wifi quickly. Added VLC and Gimp.

Installed Unbuntu Restricted drivers and so far so good. :)

---

### Post by geovino on 2011-05-18
I reinstalled and it did bring up the unity side bar for a while and then it failed to come up so I'm stuck with and regular classic desktop. Unity needs work. Maybe the next version will fix this problem.

---

### Post by Krytarik on 2011-05-18
See this guide to troubleshoot Unity:
[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

If you want to run the Cube with Unity, see this one:
[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

---

### Post by geovino on 2011-05-18
What would make the desktop effects work then after a few reboots disappear? Never had this trouble with Ubuntu before.

---

### Post by geovino on 2011-05-18
> **Krytarik said:**
> See this guide to troubleshoot Unity:
[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

If you want to run the Cube with Unity, see this one:
[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

Thanks, I'll check out the link.

Right now Unity is working, but who knows if it will be there on the next reboot.

---

### Post by Krytarik on 2011-05-18
> **geovino said:**
> What would make the desktop effects work then after a few reboots disappear?
If the Unity/Compiz check fails upon boot, you are getting automatically logged in to "Ubuntu Classic" or "Ubuntu Classic (No effects)", respectively.

When that happens, run either of these checks in a terminal to see the results:
```
/usr/lib/nux/unity_support_test -p
/usr/lib/nux/unity_support_test -p --compiz
```If those checks are delivering results inconsistently upon boot, both of these can be skipped if needed.
> **geovino said:**
> 
Maybe I should go back to 10.04 or try Mint on this laptop?
If you don't want to use Unity anyway, I indeed suggest Ubuntu 10.04, as it is a LTS version, supported until the end of April 2013. I'm still running it, I only installed it last October, and plan to run it at least until then.

---

### Post by geovino on 2011-05-18
I get this:


davek@davenet:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no
davek@davenet:~$ 

and this:


davek@davenet:~$ /usr/lib/nux/unity_support_test -p --compiz
OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes

Compiz supported:         no

How can I correct this?

---

### Post by Krytarik on 2011-05-18
So, the proprietary Nvidia driver is not running.

Is a proper xorg.conf in place?

To create a fresh, proper xorg.conf:
```
sudo nvidia-xconfig --add-argb-glx-visuals --no-logo --force-generate
```

If even with that the Nvidia driver doesn't get loaded, post the content of "/var/log/Xorg.0.log". Use the #-button in the editor to enclose it in code-tags, mark the text before pressing it.

---

### Post by geovino on 2011-05-18
> **Krytarik said:**
> So, the proprietary Nvidia driver is not running.

Is a proper xorg.conf in place?

To create a fresh, proper xorg.conf:
```
sudo nvidia-xconfig --add-argb-glx-visuals --no-logo --force-generate
```

If even with that the Nvidia driver doesn't get loaded, post the content of "/var/log/Xorg.0.log". Use the #-button in the editor to enclose it in code-tags, mark the text before pressing it.

I get this:

davek@davenet:~$ sudo nvidia-xconfig --add-argb-glx-visuals --no-logo --force-generate
[sudo] password for davek: 
sudo: nvidia-xconfig: command not found
davek@davenet:~$ 

the var log is very big, I don't think should past that in here.

---

### Post by geovino on 2011-05-18
so now it looks like every other time compiz works and then I reboot and it goes to no desktop effects. never seen this before.

---

### Post by Krytarik on 2011-05-18
> **geovino said:**
> 
davek@davenet:~$ sudo nvidia-xconfig --add-argb-glx-visuals --no-logo --force-generate
[sudo] password for davek: 
sudo: nvidia-xconfig: command not found
davek@davenet:~$ 

Is the proprietary Nvidia driver even installed!?
Check in "Additional Drivers".
> **geovino said:**
> 
the var log is very big, I don't think should past that in here.
That's why I said in code-tags, but you could also just attach it.

---

### Post by geovino on 2011-05-18
here's the logs:

[    15.700] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    15.700] X Protocol Version 11, Revision 0
[    15.700] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    15.700] Current Operating System: Linux davenet 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64
[    15.700] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=3df1375c-25be-40c5-a8fe-fb28de3afb09 ro quiet splash vt.handoff=7
[    15.700] Build Date: 19 April 2011  03:40:45PM
[    15.700] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    15.700] Current version of pixman: 0.20.2
[    15.700] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    15.700] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    15.702] (==) Log file: "/var/log/Xorg.0.log", Time: Wed May 18 16:53:03 2011
[    15.718] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    15.718] (==) No Layout section.  Using the first Screen section.
[    15.718] (==) No screen section available. Using defaults.
[    15.718] (**) |-->Screen "Default Screen Section" (0)
[    15.718] (**) |   |-->Monitor "<default monitor>"
[    15.719] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    15.719] (==) Automatically adding devices
[    15.719] (==) Automatically enabling devices
[    15.719] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    15.719] 	Entry deleted from font path.
[    15.719] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    15.719] 	Entry deleted from font path.
[    15.719] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    15.719] 	Entry deleted from font path.
[    15.719] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    15.719] 	Entry deleted from font path.
[    15.719] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    15.719] 	Entry deleted from font path.
[    15.719] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    15.719] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    15.719] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    15.719] (II) Loader magic: 0x7e0280
[    15.719] (II) Module ABI versions:
[    15.719] 	X.Org ANSI C Emulation: 0.4
[    15.719] 	X.Org Video Driver: 10.0
[    15.719] 	X.Org XInput driver : 12.3
[    15.719] 	X.Org Server Extension : 5.0
[    15.720] (--) PCI:*(0:1:5:0) 1002:791f:1025:0123 rev 0, Mem @ 0xd0000000/268435456, 0xf0100000/65536, 0xf0000000/1048576, I/O @ 0x00009000/256
[    15.721] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    15.721] (II) LoadModule: "extmod"
[    15.732] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    15.733] (II) Module extmod: vendor="X.Org Foundation"
[    15.733] 	compiled for 1.10.1, module version = 1.0.0
[    15.733] 	Module class: X.Org Server Extension
[    15.733] 	ABI class: X.Org Server Extension, version 5.0
[    15.733] (II) Loading extension MIT-SCREEN-SAVER
[    15.733] (II) Loading extension XFree86-VidModeExtension
[    15.733] (II) Loading extension XFree86-DGA
[    15.733] (II) Loading extension DPMS
[    15.733] (II) Loading extension XVideo
[    15.733] (II) Loading extension XVideo-MotionCompensation
[    15.733] (II) Loading extension X-Resource
[    15.733] (II) LoadModule: "dbe"
[    15.733] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    15.734] (II) Module dbe: vendor="X.Org Foundation"
[    15.734] 	compiled for 1.10.1, module version = 1.0.0
[    15.734] 	Module class: X.Org Server Extension
[    15.734] 	ABI class: X.Org Server Extension, version 5.0
[    15.734] (II) Loading extension DOUBLE-BUFFER
[    15.734] (II) LoadModule: "glx"
[    15.734] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    15.734] (II) Module glx: vendor="X.Org Foundation"
[    15.734] 	compiled for 1.10.1, module version = 1.0.0
[    15.734] 	ABI class: X.Org Server Extension, version 5.0
[    15.734] (==) AIGLX enabled
[    15.734] (II) Loading extension GLX
[    15.734] (II) LoadModule: "record"
[    15.735] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    15.735] (II) Module record: vendor="X.Org Foundation"
[    15.735] 	compiled for 1.10.1, module version = 1.13.0
[    15.735] 	Module class: X.Org Server Extension
[    15.735] 	ABI class: X.Org Server Extension, version 5.0
[    15.735] (II) Loading extension RECORD
[    15.735] (II) LoadModule: "dri"
[    15.736] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    15.736] (II) Module dri: vendor="X.Org Foundation"
[    15.736] 	compiled for 1.10.1, module version = 1.0.0
[    15.736] 	ABI class: X.Org Server Extension, version 5.0
[    15.736] (II) Loading extension XFree86-DRI
[    15.736] (II) LoadModule: "dri2"
[    15.737] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.737] (II) Module dri2: vendor="X.Org Foundation"
[    15.737] 	compiled for 1.10.1, module version = 1.2.0
[    15.737] 	ABI class: X.Org Server Extension, version 5.0
[    15.737] (II) Loading extension DRI2
[    15.737] (==) Matched fglrx as autoconfigured driver 0
[    15.737] (==) Matched ati as autoconfigured driver 1
[    15.737] (==) Matched vesa as autoconfigured driver 2
[    15.737] (==) Matched fbdev as autoconfigured driver 3
[    15.737] (==) Assigned the driver to the xf86ConfigLayout
[    15.737] (II) LoadModule: "fglrx"
[    15.738] (WW) Warning, couldn't open module fglrx
[    15.738] (II) UnloadModule: "fglrx"
[    15.738] (II) Unloading fglrx
[    15.738] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    15.738] (II) LoadModule: "ati"
[    15.738] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    15.738] (II) Module ati: vendor="X.Org Foundation"
[    15.738] 	compiled for 1.10.0, module version = 6.14.0
[    15.738] 	Module class: X.Org Video Driver
[    15.738] 	ABI class: X.Org Video Driver, version 10.0
[    15.738] (II) LoadModule: "radeon"
[    15.739] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    15.739] (II) Module radeon: vendor="X.Org Foundation"
[    15.739] 	compiled for 1.10.0, module version = 6.14.0
[    15.739] 	Module class: X.Org Video Driver
[    15.739] 	ABI class: X.Org Video Driver, version 10.0
[    15.739] (II) LoadModule: "vesa"
[    15.748] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    15.748] (II) Module vesa: vendor="X.Org Foundation"
[    15.748] 	compiled for 1.10.0, module version = 2.3.0
[    15.748] 	Module class: X.Org Video Driver
[    15.748] 	ABI class: X.Org Video Driver, version 10.0
[    15.748] (II) LoadModule: "fbdev"
[    15.748] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    15.748] (II) Module fbdev: vendor="X.Org Foundation"
[    15.748] 	compiled for 1.10.0, module version = 0.4.2
[    15.748] 	ABI class: X.Org Video Driver, version 10.0
[    15.749] (II) RADEON: Driver for ATI Radeon chipsets:
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
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
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
[    15.764] (II) VESA: driver for VESA chipsets: vesa
[    15.764] (II) FBDEV: driver for framebuffer: fbdev
[    15.764] (++) using VT number 7

[    15.764] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    15.764] (II) [KMS] drm report modesetting isn't supported.
[    15.764] (WW) Falling back to old probe method for vesa
[    15.764] (WW) Falling back to old probe method for fbdev
[    15.764] (II) Loading sub module "fbdevhw"
[    15.764] (II) LoadModule: "fbdevhw"
[    15.765] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    15.765] (II) Module fbdevhw: vendor="X.Org Foundation"
[    15.765] 	compiled for 1.10.1, module version = 0.0.2
[    15.765] 	ABI class: X.Org Video Driver, version 10.0
[    15.765] (II) RADEON(0): TOTO SAYS 00000000f0100000
[    15.765] (II) RADEON(0): MMIO registers at 0x00000000f0100000: size 64KB
[    15.765] (II) RADEON(0): PCI bus 1 card 5 func 0
[    15.765] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    15.765] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    15.765] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    15.765] (==) RADEON(0): Default visual is TrueColor
[    15.765] (II) Loading sub module "vgahw"
[    15.765] (II) LoadModule: "vgahw"
[    15.766] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    15.777] (II) Module vgahw: vendor="X.Org Foundation"
[    15.777] 	compiled for 1.10.1, module version = 0.1.0
[    15.777] 	ABI class: X.Org Video Driver, version 10.0
[    15.777] (II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    15.777] (==) RADEON(0): RGB weight 888
[    15.777] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    15.782] (--) RADEON(0): Chipset: "ATI Radeon X1200" (ChipID = 0x791f)
[    15.782] (--) RADEON(0): Linear framebuffer at 0x00000000d0000000
[    15.782] (II) RADEON(0): PCI card detected
[    15.782] (II) Loading sub module "int10"
[    15.782] (II) LoadModule: "int10"
[    15.783] (II) Loading /usr/lib/xorg/modules/libint10.so
[    15.861] (II) Module int10: vendor="X.Org Foundation"
[    15.861] 	compiled for 1.10.1, module version = 1.0.0
[    15.861] 	ABI class: X.Org Video Driver, version 10.0
[    15.861] (II) RADEON(0): initializing int10
[    15.862] (II) RADEON(0): Primary V_BIOS segment is: 0xc000
[    15.862] (II) RADEON(0): ATOM BIOS detected
[    15.862] (II) RADEON(0): ATOM BIOS Rom: 
[    15.862] 	SubsystemVendorID: 0x1025 SubsystemID: 0x0123
[    15.862] 	IOBaseAddress: 0x9000
[    15.862] 	Filename: BR24056Ob.bi
[    15.862] 	BIOS Bootup Message: 

ATI Radeon Xpress ?1250? for A_Orta                                         


[    15.862] (II) RADEON(0): Framebuffer space used by Firmware (kb): 20
[    15.862] (II) RADEON(0): Start of VRAM area used by Firmware: 0xfffb000
[    15.862] (II) RADEON(0): AtomBIOS requests 20kB of VRAM scratch space
[    15.862] (II) RADEON(0): AtomBIOS VRAM scratch base: 0xfffb000
[    15.862] (II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
[    15.862] (II) RADEON(0): Default Engine Clock: 400000
[    15.862] (II) RADEON(0): Default Memory Clock: 200000
[    15.862] (II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1200000
[    15.862] (II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0
[    15.862] (II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 13500
[    15.862] (II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 1000
[    15.862] (II) RADEON(0): Maximum Pixel Clock: 400000
[    15.862] (II) RADEON(0): Reference Clock: 14320
[    15.863] drmOpenDevice: node name is /dev/dri/card0
[    17.110] drmOpenByBusid: Searching for BusID pci:0000:01:05.0
[    17.110] drmOpenDevice: node name is /dev/dri/card0
[    17.110] drmOpenDevice: open result is 10, (OK)
[    17.110] drmOpenByBusid: drmOpenMinor returns 10
[    17.110] drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
[    17.110] (EE) RADEON(0): [dri] RADEONDRIGetVersion failed because of a version mismatch.
[dri] This chipset requires a kernel module version of 1.17.0,
[dri] but the kernel reports a version of 2.8.0.[dri] If using legacy modesetting, upgrade your kernel.
[dri] If using kernel modesetting, make sure your module is
[dri] loaded prior to starting X, and that this driver was built
[dri] with support for KMS.
[dri] Disabling DRI.
[    17.110] (II) RADEON(0): Generation 2 PCI interface, using max accessible memory
[    17.110] (II) RADEON(0): Detected total video RAM=262144K, accessible=262144K (PCI BAR=262144K)
[    17.110] (--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
[    17.110] (II) RADEON(0): Color tiling enabled by default
[    17.110] (II) Loading sub module "ddc"
[    17.110] (II) LoadModule: "ddc"
[    17.110] (II) Module "ddc" already built-in
[    17.110] (II) Loading sub module "i2c"
[    17.110] (II) LoadModule: "i2c"
[    17.110] (II) Module "i2c" already built-in
[    17.110] (II) RADEON(0): PLL parameters: rf=1432 rd=12 min=80000 max=120000; xclk=40000
[    17.110] (WW) RADEON(0): LVDS Info:
XRes: 1280, YRes: 800, DotClock: 69300
HBlank: 125, HOverPlus: 48, HSyncWidth: 32
VBlank: 22, VOverPlus: 3, VSyncWidth: 6
[    17.110] (II) RADEON(0): Skipping TV-Out
[    17.110] (II) RADEON(0): Output VGA-0 has no monitor section
[    17.110] (II) RADEON(0): I2C bus "VGA-0" initialized.
[    17.110] (II) RADEON(0): Output LVDS has no monitor section
[    17.110] (II) RADEON(0): I2C bus "LVDS" initialized.
[    17.110] (II) RADEON(0): Port0:
[    17.111]   XRANDR name: VGA-0
[    17.111]   Connector: VGA
[    17.111]   CRT1: INTERNAL_KLDSCP_DAC1
[    17.111]   DDC reg: 0x7e50
[    17.111] (II) RADEON(0): Port1:
[    17.111]   XRANDR name: LVDS
[    17.111]   Connector: LVDS
[    17.111]   LCD1: INTERNAL_LVTM1
[    17.111]   DDC reg: 0x7e40
[    17.111] (II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
[    17.177] Dac detection success
[    17.177] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    17.177] finished output detect: 0
[    17.177] (II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
[    17.247] (II) RADEON(0): EDID for output LVDS
[    17.293] (II) RADEON(0): Manufacturer: LPL  Model: 129  Serial#: 0
[    17.293] (II) RADEON(0): Year: 2007  Week: 0
[    17.293] (II) RADEON(0): EDID Version: 1.3
[    17.293] (II) RADEON(0): Digital Display Input
[    17.293] (II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 19
[    17.293] (II) RADEON(0): Gamma: 2.20
[    17.293] (II) RADEON(0): No DPMS capabilities specified
[    17.293] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    17.293] (II) RADEON(0): First detailed timing is preferred mode
[    17.293] (II) RADEON(0): redX: 0.584 redY: 0.347   greenX: 0.324 greenY: 0.542
[    17.293] (II) RADEON(0): blueX: 0.158 blueY: 0.145   whiteX: 0.313 whiteY: 0.329
[    17.293] (II) RADEON(0): Manufacturer's mask: 0
[    17.293] (II) RADEON(0): Supported detailed timing:
[    17.293] (II) RADEON(0): clock: 69.3 MHz   Image Size:  304 x 190 mm
[    17.293] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1405 h_border: 0
[    17.293] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 822 v_border: 0
[    17.293] (II) RADEON(0):  LGPhilipsLCD
[    17.293] (II) RADEON(0):  LP141WX3-TLN1
[    17.293] (II) RADEON(0): EDID (in hex):
[    17.293] (II) RADEON(0): 	00ffffffffffff00320c290100000000
[    17.293] (II) RADEON(0): 	00110103801e13780ab3859558538a28
[    17.293] (II) RADEON(0): 	25505400000001010101010101010101
[    17.293] (II) RADEON(0): 	010101010101121b007d502016303020
[    17.293] (II) RADEON(0): 	360030be100000180000000000000000
[    17.293] (II) RADEON(0): 	00000000000000000000000000fe004c
[    17.293] (II) RADEON(0): 	475068696c6970734c43440a000000fe
[    17.293] (II) RADEON(0): 	004c503134315758332d544c4e3100b2
[    17.293] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    17.293] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    17.293] (II) RADEON(0): Manufacturer: LPL  Model: 129  Serial#: 0
[    17.293] (II) RADEON(0): Year: 2007  Week: 0
[    17.293] (II) RADEON(0): EDID Version: 1.3
[    17.293] (II) RADEON(0): Digital Display Input
[    17.293] (II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 19
[    17.293] (II) RADEON(0): Gamma: 2.20
[    17.293] (II) RADEON(0): No DPMS capabilities specified
[    17.293] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    17.293] (II) RADEON(0): First detailed timing is preferred mode
[    17.293] (II) RADEON(0): redX: 0.584 redY: 0.347   greenX: 0.324 greenY: 0.542
[    17.293] (II) RADEON(0): blueX: 0.158 blueY: 0.145   whiteX: 0.313 whiteY: 0.329
[    17.294] (II) RADEON(0): Manufacturer's mask: 0
[    17.294] (II) RADEON(0): Supported detailed timing:
[    17.294] (II) RADEON(0): clock: 69.3 MHz   Image Size:  304 x 190 mm
[    17.294] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1405 h_border: 0
[    17.294] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 822 v_border: 0
[    17.294] (II) RADEON(0):  LGPhilipsLCD
[    17.294] (II) RADEON(0):  LP141WX3-TLN1
[    17.294] (II) RADEON(0): EDID (in hex):
[    17.294] (II) RADEON(0): 	00ffffffffffff00320c290100000000
[    17.294] (II) RADEON(0): 	00110103801e13780ab3859558538a28
[    17.294] (II) RADEON(0): 	25505400000001010101010101010101
[    17.294] (II) RADEON(0): 	010101010101121b007d502016303020
[    17.294] (II) RADEON(0): 	360030be100000180000000000000000
[    17.294] (II) RADEON(0): 	00000000000000000000000000fe004c
[    17.294] (II) RADEON(0): 	475068696c6970734c43440a000000fe
[    17.294] (II) RADEON(0): 	004c503134315758332d544c4e3100b2
[    17.294] finished output detect: 1
[    17.294] finished all detect
[    17.360] Dac detection success
[    17.360] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    17.360] (II) RADEON(0): EDID for output VGA-0
[    17.417] (II) RADEON(0): EDID for output LVDS
[    17.417] (II) RADEON(0): Manufacturer: LPL  Model: 129  Serial#: 0
[    17.417] (II) RADEON(0): Year: 2007  Week: 0
[    17.417] (II) RADEON(0): EDID Version: 1.3
[    17.417] (II) RADEON(0): Digital Display Input
[    17.417] (II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 19
[    17.417] (II) RADEON(0): Gamma: 2.20
[    17.417] (II) RADEON(0): No DPMS capabilities specified
[    17.417] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    17.417] (II) RADEON(0): First detailed timing is preferred mode
[    17.417] (II) RADEON(0): redX: 0.584 redY: 0.347   greenX: 0.324 greenY: 0.542
[    17.417] (II) RADEON(0): blueX: 0.158 blueY: 0.145   whiteX: 0.313 whiteY: 0.329
[    17.417] (II) RADEON(0): Manufacturer's mask: 0
[    17.417] (II) RADEON(0): Supported detailed timing:
[    17.417] (II) RADEON(0): clock: 69.3 MHz   Image Size:  304 x 190 mm
[    17.417] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1405 h_border: 0
[    17.417] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 822 v_border: 0
[    17.417] (II) RADEON(0):  LGPhilipsLCD
[    17.417] (II) RADEON(0):  LP141WX3-TLN1
[    17.417] (II) RADEON(0): EDID (in hex):
[    17.417] (II) RADEON(0): 	00ffffffffffff00320c290100000000
[    17.417] (II) RADEON(0): 	00110103801e13780ab3859558538a28
[    17.417] (II) RADEON(0): 	25505400000001010101010101010101
[    17.417] (II) RADEON(0): 	010101010101121b007d502016303020
[    17.417] (II) RADEON(0): 	360030be100000180000000000000000
[    17.417] (II) RADEON(0): 	00000000000000000000000000fe004c
[    17.417] (II) RADEON(0): 	475068696c6970734c43440a000000fe
[    17.417] (II) RADEON(0): 	004c503134315758332d544c4e3100b2
[    17.417] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    17.417] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    17.417] (II) RADEON(0): Manufacturer: LPL  Model: 129  Serial#: 0
[    17.417] (II) RADEON(0): Year: 2007  Week: 0
[    17.417] (II) RADEON(0): EDID Version: 1.3
[    17.417] (II) RADEON(0): Digital Display Input
[    17.417] (II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 19
[    17.417] (II) RADEON(0): Gamma: 2.20
[    17.417] (II) RADEON(0): No DPMS capabilities specified
[    17.417] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    17.417] (II) RADEON(0): First detailed timing is preferred mode
[    17.417] (II) RADEON(0): redX: 0.584 redY: 0.347   greenX: 0.324 greenY: 0.542
[    17.418] (II) RADEON(0): blueX: 0.158 blueY: 0.145   whiteX: 0.313 whiteY: 0.329
[    17.418] (II) RADEON(0): Manufacturer's mask: 0
[    17.418] (II) RADEON(0): Supported detailed timing:
[    17.418] (II) RADEON(0): clock: 69.3 MHz   Image Size:  304 x 190 mm
[    17.418] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1405 h_border: 0
[    17.418] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 822 v_border: 0
[    17.418] (II) RADEON(0):  LGPhilipsLCD
[    17.418] (II) RADEON(0):  LP141WX3-TLN1
[    17.418] (II) RADEON(0): EDID (in hex):
[    17.418] (II) RADEON(0): 	00ffffffffffff00320c290100000000
[    17.418] (II) RADEON(0): 	00110103801e13780ab3859558538a28
[    17.418] (II) RADEON(0): 	25505400000001010101010101010101
[    17.418] (II) RADEON(0): 	010101010101121b007d502016303020
[    17.418] (II) RADEON(0): 	360030be100000180000000000000000
[    17.418] (II) RADEON(0): 	00000000000000000000000000fe004c
[    17.418] (II) RADEON(0): 	475068696c6970734c43440a000000fe
[    17.418] (II) RADEON(0): 	004c503134315758332d544c4e3100b2
[    17.418] (II) RADEON(0): EDID vendor "LPL", prod id 297
[    17.418] (II) RADEON(0): Printing probed modes for output LVDS
[    17.418] (II) RADEON(0): Modeline "1280x800"x60.0   69.30  1280 1328 1360 1405  800 803 809 822 -hsync -vsync (49.3 kHz)
[    17.418] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    17.418] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    17.418] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    17.418] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    17.418] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    17.418] (II) RADEON(0): Output VGA-0 disconnected
[    17.418] (II) RADEON(0): Output LVDS connected
[    17.418] (II) RADEON(0): Using exact sizes for initial modes
[    17.418] (II) RADEON(0): Output LVDS using initial mode 1280x800
[    17.418] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    17.418] (==) RADEON(0): DPI set to (96, 96)
[    17.418] (II) Loading sub module "fb"
[    17.418] (II) LoadModule: "fb"
[    17.419] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.419] (II) Module fb: vendor="X.Org Foundation"
[    17.419] 	compiled for 1.10.1, module version = 1.0.0
[    17.419] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    17.419] (II) Loading sub module "ramdac"
[    17.419] (II) LoadModule: "ramdac"
[    17.419] (II) Module "ramdac" already built-in
[    17.419] (==) RADEON(0): Using XAA acceleration architecture
[    17.419] (II) Loading sub module "xaa"
[    17.419] (II) LoadModule: "xaa"
[    17.420] (II) Loading /usr/lib/xorg/modules/libxaa.so
[    17.591] (II) Module xaa: vendor="X.Org Foundation"
[    17.591] 	compiled for 1.10.1, module version = 1.2.1
[    17.591] 	ABI class: X.Org Video Driver, version 10.0
[    17.591] (!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
[    17.591] (II) UnloadModule: "vesa"
[    17.591] (II) Unloading vesa
[    17.591] (II) UnloadModule: "fbdev"
[    17.591] (II) Unloading fbdev
[    17.591] (II) UnloadModule: "fbdevhw"
[    17.591] (II) Unloading fbdevhw
[    17.591] (--) Depth 24 pixmap format is 32 bpp
[    17.591] (II) RADEON(0): RADEONScreenInit d0000000 0 0
[    17.617] Output LCD1 disable success
[    17.617] Blank CRTC 0 success
[    17.617] Disable CRTC 0 success
[    17.617] Blank CRTC 1 success
[    17.618] Disable CRTC 1 success
[    17.618] (II) RADEON(0): Dynamic Power Management Disabled
[    17.618] (II) RADEON(0): RADEONInitMemoryMap() : 
[    17.618] (II) RADEON(0):   mem_size         : 0x10000000
[    17.618] (II) RADEON(0):   MC_FB_LOCATION   : 0xbfffb000
[    17.618] (II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
[    17.618] (II) RADEON(0): Depth moves disabled by default
[    17.618] (II) RADEON(0): Memory manager initialized to (0,0) (1280,8191)
[    17.618] (II) RADEON(0): Reserved area from (0,1280) to (1280,1282)
[    17.618] (II) RADEON(0): Largest offscreen area available: 1280 x 6909
[    17.618] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    17.618] (II) RADEON(0):   MC_FB_LOCATION   : 0xbfffb000 0xbfffb000
[    17.618] (II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
[    17.628] (==) RADEON(0): Backing store disabled
[    17.628] (WW) RADEON(0): Direct rendering disabled
[    17.628] (II) RADEON(0): Render acceleration disabled
[    17.628] (II) RADEON(0): num quad-pipes is 1
[    17.628] (II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
[    17.628] 	Screen to screen bit blits
[    17.628] 	Solid filled rectangles
[    17.628] 	8x8 mono pattern filled rectangles
[    17.628] 	Indirect CPU to Screen color expansion
[    17.628] 	Solid Lines
[    17.628] 	Scanline Image Writes
[    17.628] 	Setting up tile and stipple cache:
[    17.629] 		32 128x128 slots
[    17.629] 		32 256x256 slots
[    17.629] 		16 512x512 slots
[    17.631] (II) RADEON(0): Acceleration enabled
[    17.631] (==) RADEON(0): DPMS enabled
[    17.631] (==) RADEON(0): Silken mouse enabled
[    17.631] (II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00643000
[    17.631] (II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00648000
[    17.632] (II) RADEON(0): Largest offscreen area available: 1280 x 6901
[    17.632] (II) RADEON(0): Textured video requires CP on R5xx/R6xx/R7xx/IGP
[    17.646] Output CRT1 disable success
[    17.646] Output LCD1 disable success
[    17.646] Blank CRTC 0 success
[    17.646] Disable CRTC 0 success
[    17.646] Blank CRTC 1 success
[    17.646] Disable CRTC 1 success
[    17.646] Output LCD1 disable success
[    17.646] Blank CRTC 0 success
[    17.646] Disable CRTC 0 success
[    17.646] Set CRTC 0 Source success
[    17.646] Mode 1280x800 - 1405 822 10
[    17.646] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    17.646] (II) RADEON(0):   MC_FB_LOCATION   : 0xbfffb000 0xbfffb000
[    17.646] (II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
[    17.646] Picked PLL 0
[    17.646] best_freq: 69353
[    17.646] best_feedback_div: 247
[    17.646] best_frac_feedback_div: 0
[    17.646] best_ref_div: 3
[    17.646] best_post_div: 17
[    17.646] (II) RADEON(0): crtc(0) Clock: mode 69300, PLL 693530
[    17.646] (II) RADEON(0): crtc(0) PLL  : refdiv 3, fbdiv 0xF7(247), fracfbdiv 0, pdiv 17
[    17.649] Set CRTC 0 PLL success
[    17.649] Set CRTC Timing success
[    17.649] Set CRTC 0 Overscan success
[    17.649] Not using RMX
[    17.649] scaler 0 setup success
[    17.649] Set CRTC 0 Source success
[    17.649] crtc 0 YUV disable setup success
[    17.650] Output digital setup success
[    17.651] Output LCD1 enable success
[    17.651] Enable CRTC 0 success
[    17.651] Unblank CRTC 0 success
[    17.651] Output CRT1 disable success
[    17.651] Blank CRTC 1 success
[    17.651] Disable CRTC 1 success
[    17.651] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    17.652] (--) RandR disabled
[    17.652] (II) Initializing built-in extension Generic Event Extension
[    17.652] (II) Initializing built-in extension SHAPE
[    17.652] (II) Initializing built-in extension MIT-SHM
[    17.652] (II) Initializing built-in extension XInputExtension
[    17.652] (II) Initializing built-in extension XTEST
[    17.652] (II) Initializing built-in extension BIG-REQUESTS
[    17.652] (II) Initializing built-in extension SYNC
[    17.652] (II) Initializing built-in extension XKEYBOARD
[    17.652] (II) Initializing built-in extension XC-MISC
[    17.652] (II) Initializing built-in extension SECURITY
[    17.652] (II) Initializing built-in extension XINERAMA
[    17.652] (II) Initializing built-in extension XFIXES
[    17.652] (II) Initializing built-in extension RENDER
[    17.652] (II) Initializing built-in extension RANDR
[    17.652] (II) Initializing built-in extension COMPOSITE
[    17.652] (II) Initializing built-in extension DAMAGE
[    17.652] (II) Initializing built-in extension GESTURE
[    17.662] (II) AIGLX: Screen 0 is not DRI2 capable
[    17.662] (II) AIGLX: Screen 0 is not DRI capable
[    17.662] (II) AIGLX: Trying DRI driver /usr/lib/dri/swrast_dri.so
[    17.701] (II) AIGLX: Loaded and initialized swrast
[    17.701] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    17.701] (II) RADEON(0): Setting screen physical size to 338 x 211
[    17.717] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    17.732] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    17.732] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    17.732] (II) LoadModule: "evdev"
[    17.733] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.734] (II) Module evdev: vendor="X.Org Foundation"
[    17.734] 	compiled for 1.10.0.902, module version = 2.6.0
[    17.734] 	Module class: X.Org XInput Driver
[    17.734] 	ABI class: X.Org XInput driver, version 12.3
[    17.734] (II) Using input driver 'evdev' for 'Power Button'
[    17.734] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.734] (**) Power Button: always reports core events
[    17.734] (**) Power Button: Device: "/dev/input/event3"
[    17.760] (--) Power Button: Found keys
[    17.831] (II) Power Button: Configuring as keyboard
[    17.831] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    17.831] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    17.831] (**) Option "xkb_rules" "evdev"
[    17.831] (**) Option "xkb_model" "pc105"
[    17.831] (**) Option "xkb_layout" "us"
[    17.850] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    17.850] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    17.850] (II) Using input driver 'evdev' for 'Video Bus'
[    17.850] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.850] (**) Video Bus: always reports core events
[    17.850] (**) Video Bus: Device: "/dev/input/event5"
[    17.880] (--) Video Bus: Found keys
[    17.880] (II) Video Bus: Configuring as keyboard
[    17.880] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1d/LNXVIDEO:01/input/input5/event5"
[    17.880] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    17.880] (**) Option "xkb_rules" "evdev"
[    17.880] (**) Option "xkb_model" "pc105"
[    17.880] (**) Option "xkb_layout" "us"
[    17.881] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    17.881] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    17.881] (II) Using input driver 'evdev' for 'Power Button'
[    17.881] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.881] (**) Power Button: always reports core events
[    17.881] (**) Power Button: Device: "/dev/input/event0"
[    17.910] (--) Power Button: Found keys
[    17.910] (II) Power Button: Configuring as keyboard
[    17.910] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    17.910] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    17.910] (**) Option "xkb_rules" "evdev"
[    17.910] (**) Option "xkb_model" "pc105"
[    17.910] (**) Option "xkb_layout" "us"
[    17.911] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    17.911] (II) No input driver/identifier specified (ignoring)
[    17.911] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    17.911] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    17.911] (II) Using input driver 'evdev' for 'Sleep Button'
[    17.911] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.911] (**) Sleep Button: always reports core events
[    17.911] (**) Sleep Button: Device: "/dev/input/event2"
[    17.950] (--) Sleep Button: Found keys
[    17.950] (II) Sleep Button: Configuring as keyboard
[    17.950] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    17.950] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    17.950] (**) Option "xkb_rules" "evdev"
[    17.950] (**) Option "xkb_model" "pc105"
[    17.950] (**) Option "xkb_layout" "us"
[    17.955] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v1.0 (/dev/input/event7)
[    17.955] (**) Microsoft Microsoft® Nano Transceiver v1.0: Applying InputClass "evdev keyboard catchall"
[    17.955] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Nano Transceiver v1.0'
[    17.955] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.955] (**) Microsoft Microsoft® Nano Transceiver v1.0: always reports core events
[    17.956] (**) Microsoft Microsoft® Nano Transceiver v1.0: Device: "/dev/input/event7"
[    17.980] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found keys
[    17.980] (II) Microsoft Microsoft® Nano Transceiver v1.0: Configuring as keyboard
[    17.980] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb2/2-2/2-2:1.0/input/input7/event7"
[    17.980] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v1.0" (type: KEYBOARD)
[    17.980] (**) Option "xkb_rules" "evdev"
[    17.980] (**) Option "xkb_model" "pc105"
[    17.980] (**) Option "xkb_layout" "us"
[    17.981] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v1.0 (/dev/input/event8)
[    17.981] (**) Microsoft Microsoft® Nano Transceiver v1.0: Applying InputClass "evdev pointer catchall"
[    17.981] (**) Microsoft Microsoft® Nano Transceiver v1.0: Applying InputClass "evdev keyboard catchall"
[    17.981] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Nano Transceiver v1.0'
[    17.981] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.981] (**) Microsoft Microsoft® Nano Transceiver v1.0: always reports core events
[    17.981] (**) Microsoft Microsoft® Nano Transceiver v1.0: Device: "/dev/input/event8"
[    18.020] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found 9 mouse buttons
[    18.020] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found scroll wheel(s)
[    18.020] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found relative axes
[    18.020] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found x and y relative axes
[    18.020] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found absolute axes
[    18.020] (II) evdev-grail: failed to open grail, no gesture support
[    18.020] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found keys
[    18.020] (II) Microsoft Microsoft® Nano Transceiver v1.0: Configuring as mouse
[    18.020] (II) Microsoft Microsoft® Nano Transceiver v1.0: Configuring as keyboard
[    18.020] (II) Microsoft Microsoft® Nano Transceiver v1.0: Adding scrollwheel support
[    18.020] (**) Microsoft Microsoft® Nano Transceiver v1.0: YAxisMapping: buttons 4 and 5
[    18.020] (**) Microsoft Microsoft® Nano Transceiver v1.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.020] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb2/2-2/2-2:1.1/input/input8/event8"
[    18.020] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v1.0" (type: KEYBOARD)
[    18.020] (**) Option "xkb_rules" "evdev"
[    18.020] (**) Option "xkb_model" "pc105"
[    18.020] (**) Option "xkb_layout" "us"
[    18.020] (II) Microsoft Microsoft® Nano Transceiver v1.0: initialized for relative axes.
[    18.020] (WW) Microsoft Microsoft® Nano Transceiver v1.0: ignoring absolute axes.
[    18.021] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) keeping acceleration scheme 1
[    18.021] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) acceleration profile 0
[    18.021] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) acceleration factor: 2.000
[    18.021] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) acceleration threshold: 4
[    18.021] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v1.0 (/dev/input/mouse0)
[    18.021] (II) No input driver/identifier specified (ignoring)
[    18.022] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v1.0 (/dev/input/event9)
[    18.022] (**) Microsoft Microsoft® Nano Transceiver v1.0: Applying InputClass "evdev keyboard catchall"
[    18.022] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Nano Transceiver v1.0'
[    18.022] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.022] (**) Microsoft Microsoft® Nano Transceiver v1.0: always reports core events
[    18.022] (**) Microsoft Microsoft® Nano Transceiver v1.0: Device: "/dev/input/event9"
[    18.040] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found 1 mouse buttons
[    18.040] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found scroll wheel(s)
[    18.040] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found relative axes
[    18.040] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found absolute axes
[    18.041] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found x and y absolute axes
[    18.041] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found keys
[    18.041] (II) Microsoft Microsoft® Nano Transceiver v1.0: Configuring as mouse
[    18.041] (II) Microsoft Microsoft® Nano Transceiver v1.0: Configuring as keyboard
[    18.041] (II) Microsoft Microsoft® Nano Transceiver v1.0: Adding scrollwheel support
[    18.041] (**) Microsoft Microsoft® Nano Transceiver v1.0: YAxisMapping: buttons 4 and 5
[    18.041] (**) Microsoft Microsoft® Nano Transceiver v1.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.041] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb2/2-2/2-2:1.2/input/input9/event9"
[    18.041] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v1.0" (type: KEYBOARD)
[    18.041] (**) Option "xkb_rules" "evdev"
[    18.041] (**) Option "xkb_model" "pc105"
[    18.041] (**) Option "xkb_layout" "us"
[    18.042] (EE) Microsoft Microsoft® Nano Transceiver v1.0: failed to initialize for relative axes.
[    18.046] (WW) Touch X valuator does not match pointer X valuator, pointer emulation may be incorrect
[    18.046] (WW) Touch Y valuator does not match pointer Y valuator, pointer emulation may be incorrect
[    18.046] (II) Microsoft Microsoft® Nano Transceiver v1.0: initialized for absolute axes.
[    18.046] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) keeping acceleration scheme 1
[    18.046] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) acceleration profile 0
[    18.046] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) acceleration factor: 2.000
[    18.046] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) acceleration threshold: 4
[    18.047] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v1.0 (/dev/input/js0)
[    18.047] (II) No input driver/identifier specified (ignoring)
[    18.049] (II) config/udev: Adding input device Acer CrystalEye webcam (/dev/input/event6)
[    18.049] (**) Acer CrystalEye webcam: Applying InputClass "evdev keyboard catchall"
[    18.049] (II) Using input driver 'evdev' for 'Acer CrystalEye webcam'
[    18.049] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.049] (**) Acer CrystalEye webcam: always reports core events
[    18.049] (**) Acer CrystalEye webcam: Device: "/dev/input/event6"
[    18.050] (--) Acer CrystalEye webcam: Found keys
[    18.050] (II) Acer CrystalEye webcam: Configuring as keyboard
[    18.050] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.5/usb1/1-7/1-7:1.0/input/input6/event6"
[    18.050] (II) XINPUT: Adding extended input device "Acer CrystalEye webcam" (type: KEYBOARD)
[    18.050] (**) Option "xkb_rules" "evdev"
[    18.050] (**) Option "xkb_model" "pc105"
[    18.050] (**) Option "xkb_layout" "us"
[    18.052] (II) config/udev: Adding input device HDA ATI SB Headphone (/dev/input/event11)
[    18.052] (II) No input driver/identifier specified (ignoring)
[    18.055] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    18.055] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    18.055] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    18.055] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.055] (**) AT Translated Set 2 keyboard: always reports core events
[    18.055] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    18.055] (--) AT Translated Set 2 keyboard: Found keys
[    18.055] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    18.055] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    18.055] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    18.055] (**) Option "xkb_rules" "evdev"
[    18.055] (**) Option "xkb_model" "pc105"
[    18.055] (**) Option "xkb_layout" "us"
[    18.056] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event10)
[    18.056] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    18.056] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    18.056] (II) LoadModule: "synaptics"
[    18.057] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    18.057] (II) Module synaptics: vendor="X.Org Foundation"
[    18.057] 	compiled for 1.10.0.902, module version = 1.3.99
[    18.057] 	Module class: X.Org XInput Driver
[    18.057] 	ABI class: X.Org XInput driver, version 12.3
[    18.057] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    18.057] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    18.057] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    18.057] (**) Option "Device" "/dev/input/event10"
[    18.070] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    18.070] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    18.070] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    18.070] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    18.070] (--) SynPS/2 Synaptics TouchPad: buttons: left right scroll-buttons
[    18.090] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    18.090] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    18.100] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input10/event10"
[    18.100] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    18.100] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    18.100] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    18.100] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    18.100] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    18.100] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    18.100] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    18.100] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    18.120] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[    18.120] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    18.120] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    18.120] (II) No input driver/identifier specified (ignoring)
[    18.879] Dac detection success
[    18.879] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    18.935] (II) RADEON(0): EDID vendor "LPL", prod id 297
[    18.935] (II) RADEON(0): Printing DDC gathered Modelines:
[    18.935] (II) RADEON(0): Modeline "1280x800"x0.0   69.30  1280 1328 1360 1405  800 803 809 822 -hsync -vsync (49.3 kHz)
[    18.935] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    18.935] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    18.935] (II) RADEON(0): Manufacturer: LPL  Model: 129  Serial#: 0
[    18.935] (II) RADEON(0): Year: 2007  Week: 0
[    18.935] (II) RADEON(0): EDID Version: 1.3
[    18.935] (II) RADEON(0): Digital Display Input
[    18.935] (II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 19
[    18.935] (II) RADEON(0): Gamma: 2.20
[    18.935] (II) RADEON(0): No DPMS capabilities specified
[    18.935] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    18.935] (II) RADEON(0): First detailed timing is preferred mode
[    18.935] (II) RADEON(0): redX: 0.584 redY: 0.347   greenX: 0.324 greenY: 0.542
[    18.935] (II) RADEON(0): blueX: 0.158 blueY: 0.145   whiteX: 0.313 whiteY: 0.329
[    18.935] (II) RADEON(0): Manufacturer's mask: 0
[    18.935] (II) RADEON(0): Supported detailed timing:
[    18.935] (II) RADEON(0): clock: 69.3 MHz   Image Size:  304 x 190 mm
[    18.935] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1405 h_border: 0
[    18.935] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 822 v_border: 0
[    18.935] (II) RADEON(0):  LGPhilipsLCD
[    18.935] (II) RADEON(0):  LP141WX3-TLN1
[    18.935] (II) RADEON(0): EDID (in hex):
[    18.935] (II) RADEON(0): 	00ffffffffffff00320c290100000000
[    18.935] (II) RADEON(0): 	00110103801e13780ab3859558538a28
[    18.936] (II) RADEON(0): 	25505400000001010101010101010101
[    18.936] (II) RADEON(0): 	010101010101121b007d502016303020
[    18.936] (II) RADEON(0): 	360030be100000180000000000000000
[    18.936] (II) RADEON(0): 	00000000000000000000000000fe004c
[    18.936] (II) RADEON(0): 	475068696c6970734c43440a000000fe
[    18.936] (II) RADEON(0): 	004c503134315758332d544c4e3100b2
[    18.936] (II) RADEON(0): EDID vendor "LPL", prod id 297
[    18.958] Dac detection success
[    18.958] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    19.014] (II) RADEON(0): EDID vendor "LPL", prod id 297
[    19.014] (II) RADEON(0): Printing DDC gathered Modelines:
[    19.014] (II) RADEON(0): Modeline "1280x800"x0.0   69.30  1280 1328 1360 1405  800 803 809 822 -hsync -vsync (49.3 kHz)
[    19.014] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    19.014] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    19.014] (II) RADEON(0): Manufacturer: LPL  Model: 129  Serial#: 0
[    19.014] (II) RADEON(0): Year: 2007  Week: 0
[    19.014] (II) RADEON(0): EDID Version: 1.3
[    19.014] (II) RADEON(0): Digital Display Input
[    19.014] (II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 19
[    19.014] (II) RADEON(0): Gamma: 2.20
[    19.014] (II) RADEON(0): No DPMS capabilities specified
[    19.014] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    19.014] (II) RADEON(0): First detailed timing is preferred mode
[    19.014] (II) RADEON(0): redX: 0.584 redY: 0.347   greenX: 0.324 greenY: 0.542
[    19.015] (II) RADEON(0): blueX: 0.158 blueY: 0.145   whiteX: 0.313 whiteY: 0.329
[    19.015] (II) RADEON(0): Manufacturer's mask: 0
[    19.015] (II) RADEON(0): Supported detailed timing:
[    19.015] (II) RADEON(0): clock: 69.3 MHz   Image Size:  304 x 190 mm
[    19.015] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1405 h_border: 0
[    19.015] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 822 v_border: 0
[    19.015] (II) RADEON(0):  LGPhilipsLCD
[    19.015] (II) RADEON(0):  LP141WX3-TLN1
[    19.015] (II) RADEON(0): EDID (in hex):
[    19.015] (II) RADEON(0): 	00ffffffffffff00320c290100000000
[    19.015] (II) RADEON(0): 	00110103801e13780ab3859558538a28
[    19.015] (II) RADEON(0): 	25505400000001010101010101010101
[    19.015] (II) RADEON(0): 	010101010101121b007d502016303020
[    19.015] (II) RADEON(0): 	360030be100000180000000000000000
[    19.015] (II) RADEON(0): 	00000000000000000000000000fe004c
[    19.015] (II) RADEON(0): 	475068696c6970734c43440a000000fe
[    19.015] (II) RADEON(0): 	004c503134315758332d544c4e3100b2
[    19.015] (II) RADEON(0): EDID vendor "LPL", prod id 297
[    19.037] Dac detection success
[    19.037] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    19.093] (II) RADEON(0): EDID vendor "LPL", prod id 297
[    19.093] (II) RADEON(0): Printing DDC gathered Modelines:
[    19.093] (II) RADEON(0): Modeline "1280x800"x0.0   69.30  1280 1328 1360 1405  800 803 809 822 -hsync -vsync (49.3 kHz)
[    19.093] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    19.093] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    19.093] (II) RADEON(0): Manufacturer: LPL  Model: 129  Serial#: 0
[    19.093] (II) RADEON(0): Year: 2007  Week: 0
[    19.093] (II) RADEON(0): EDID Version: 1.3
[    19.093] (II) RADEON(0): Digital Display Input
[    19.093] (II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 19
[    19.093] (II) RADEON(0): Gamma: 2.20
[    19.093] (II) RADEON(0): No DPMS capabilities specified
[    19.093] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    19.093] (II) RADEON(0): First detailed timing is preferred mode
[    19.093] (II) RADEON(0): redX: 0.584 redY: 0.347   greenX: 0.324 greenY: 0.542
[    19.093] (II) RADEON(0): blueX: 0.158 blueY: 0.145   whiteX: 0.313 whiteY: 0.329
[    19.093] (II) RADEON(0): Manufacturer's mask: 0
[    19.093] (II) RADEON(0): Supported detailed timing:
[    19.093] (II) RADEON(0): clock: 69.3 MHz   Image Size:  304 x 190 mm
[    19.093] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1405 h_border: 0
[    19.093] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 822 v_border: 0
[    19.093] (II) RADEON(0):  LGPhilipsLCD
[    19.093] (II) RADEON(0):  LP141WX3-TLN1
[    19.093] (II) RADEON(0): EDID (in hex):
[    19.093] (II) RADEON(0): 	00ffffffffffff00320c290100000000
[    19.093] (II) RADEON(0): 	00110103801e13780ab3859558538a28
[    19.093] (II) RADEON(0): 	25505400000001010101010101010101
[    19.093] (II) RADEON(0): 	010101010101121b007d502016303020
[    19.093] (II) RADEON(0): 	360030be100000180000000000000000
[    19.093] (II) RADEON(0): 	00000000000000000000000000fe004c
[    19.093] (II) RADEON(0): 	475068696c6970734c43440a000000fe
[    19.094] (II) RADEON(0): 	004c503134315758332d544c4e3100b2
[    19.094] (II) RADEON(0): EDID vendor "LPL", prod id 297
[    19.115] Dac detection success
[    19.115] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    19.171] (II) RADEON(0): EDID vendor "LPL", prod id 297
[    19.171] (II) RADEON(0): Printing DDC gathered Modelines:
[    19.171] (II) RADEON(0): Modeline "1280x800"x0.0   69.30  1280 1328 1360 1405  800 803 809 822 -hsync -vsync (49.3 kHz)
[    19.171] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    19.171] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    19.171] (II) RADEON(0): Manufacturer: LPL  Model: 129  Serial#: 0
[    19.171] (II) RADEON(0): Year: 2007  Week: 0
[    19.171] (II) RADEON(0): EDID Version: 1.3
[    19.171] (II) RADEON(0): Digital Display Input
[    19.171] (II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 19
[    19.171] (II) RADEON(0): Gamma: 2.20
[    19.171] (II) RADEON(0): No DPMS capabilities specified
[    19.171] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    19.171] (II) RADEON(0): First detailed timing is preferred mode
[    19.171] (II) RADEON(0): redX: 0.584 redY: 0.347   greenX: 0.324 greenY: 0.542
[    19.171] (II) RADEON(0): blueX: 0.158 blueY: 0.145   whiteX: 0.313 whiteY: 0.329
[    19.171] (II) RADEON(0): Manufacturer's mask: 0
[    19.171] (II) RADEON(0): Supported detailed timing:
[    19.171] (II) RADEON(0): clock: 69.3 MHz   Image Size:  304 x 190 mm
[    19.171] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1405 h_border: 0
[    19.171] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 822 v_border: 0
[    19.171] (II) RADEON(0):  LGPhilipsLCD
[    19.171] (II) RADEON(0):  LP141WX3-TLN1
[    19.171] (II) RADEON(0): EDID (in hex):
[    19.171] (II) RADEON(0): 	00ffffffffffff00320c290100000000
[    19.171] (II) RADEON(0): 	00110103801e13780ab3859558538a28
[    19.171] (II) RADEON(0): 	25505400000001010101010101010101
[    19.171] (II) RADEON(0): 	010101010101121b007d502016303020
[    19.171] (II) RADEON(0): 	360030be100000180000000000000000
[    19.171] (II) RADEON(0): 	00000000000000000000000000fe004c
[    19.172] (II) RADEON(0): 	475068696c6970734c43440a000000fe
[    19.172] (II) RADEON(0): 	004c503134315758332d544c4e3100b2
[    19.172] (II) RADEON(0): EDID vendor "LPL", prod id 297
[    26.274] Dac detection success
[    26.274] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    26.330] (II) RADEON(0): EDID vendor "LPL", prod id 297
[    26.330] (II) RADEON(0): Printing DDC gathered Modelines:
[    26.330] (II) RADEON(0): Modeline "1280x800"x0.0   69.30  1280 1328 1360 1405  800 803 809 822 -hsync -vsync (49.3 kHz)
[    26.330] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    26.330] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    26.330] (II) RADEON(0): Manufacturer: LPL  Model: 129  Serial#: 0
[    26.330] (II) RADEON(0): Year: 2007  Week: 0
[    26.330] (II) RADEON(0): EDID Version: 1.3
[    26.330] (II) RADEON(0): Digital Display Input
[    26.330] (II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 19
[    26.330] (II) RADEON(0): Gamma: 2.20
[    26.330] (II) RADEON(0): No DPMS capabilities specified
[    26.330] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    26.330] (II) RADEON(0): First detailed timing is preferred mode
[    26.330] (II) RADEON(0): redX: 0.584 redY: 0.347   greenX: 0.324 greenY: 0.542
[    26.330] (II) RADEON(0): blueX: 0.158 blueY: 0.145   whiteX: 0.313 whiteY: 0.329
[    26.330] (II) RADEON(0): Manufacturer's mask: 0
[    26.330] (II) RADEON(0): Supported detailed timing:
[    26.330] (II) RADEON(0): clock: 69.3 MHz   Image Size:  304 x 190 mm
[    26.330] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1405 h_border: 0
[    26.330] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 822 v_border: 0
[    26.330] (II) RADEON(0):  LGPhilipsLCD
[    26.330] (II) RADEON(0):  LP141WX3-TLN1
[    26.330] (II) RADEON(0): EDID (in hex):
[    26.330] (II) RADEON(0): 	00ffffffffffff00320c290100000000
[    26.330] (II) RADEON(0): 	00110103801e13780ab3859558538a28
[    26.330] (II) RADEON(0): 	25505400000001010101010101010101
[    26.330] (II) RADEON(0): 	010101010101121b007d502016303020
[    26.330] (II) RADEON(0): 	360030be100000180000000000000000
[    26.331] (II) RADEON(0): 	00000000000000000000000000fe004c
[    26.331] (II) RADEON(0): 	475068696c6970734c43440a000000fe
[    26.331] (II) RADEON(0): 	004c503134315758332d544c4e3100b2
[    26.331] (II) RADEON(0): EDID vendor "LPL", prod id 297
[    26.353] Dac detection success
[    26.353] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    26.409] (II) RADEON(0): EDID vendor "LPL", prod id 297
[    26.409] (II) RADEON(0): Printing DDC gathered Modelines:
[    26.409] (II) RADEON(0): Modeline "1280x800"x0.0   69.30  1280 1328 1360 1405  800 803 809 822 -hsync -vsync (49.3 kHz)
[    26.409] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    26.409] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    26.409] (II) RADEON(0): Manufacturer: LPL  Model: 129  Serial#: 0
[    26.409] (II) RADEON(0): Year: 2007  Week: 0
[    26.409] (II) RADEON(0): EDID Version: 1.3
[    26.409] (II) RADEON(0): Digital Display Input
[    26.409] (II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 19
[    26.409] (II) RADEON(0): Gamma: 2.20
[    26.409] (II) RADEON(0): No DPMS capabilities specified
[    26.409] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    26.409] (II) RADEON(0): First detailed timing is preferred mode
[    26.409] (II) RADEON(0): redX: 0.584 redY: 0.347   greenX: 0.324 greenY: 0.542
[    26.409] (II) RADEON(0): blueX: 0.158 blueY: 0.145   whiteX: 0.313 whiteY: 0.329
[    26.409] (II) RADEON(0): Manufacturer's mask: 0
[    26.409] (II) RADEON(0): Supported detailed timing:
[    26.409] (II) RADEON(0): clock: 69.3 MHz   Image Size:  304 x 190 mm
[    26.409] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1405 h_border: 0
[    26.409] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 822 v_border: 0
[    26.409] (II) RADEON(0):  LGPhilipsLCD
[    26.409] (II) RADEON(0):  LP141WX3-TLN1
[    26.409] (II) RADEON(0): EDID (in hex):
[    26.409] (II) RADEON(0): 	00ffffffffffff00320c290100000000
[    26.409] (II) RADEON(0): 	00110103801e13780ab3859558538a28
[    26.409] (II) RADEON(0): 	25505400000001010101010101010101
[    26.409] (II) RADEON(0): 	010101010101121b007d502016303020
[    26.409] (II) RADEON(0): 	360030be100000180000000000000000
[    26.409] (II) RADEON(0): 	00000000000000000000000000fe004c
[    26.409] (II) RADEON(0): 	475068696c6970734c43440a000000fe
[    26.409] (II) RADEON(0): 	004c503134315758332d544c4e3100b2
[    26.409] (II) RADEON(0): EDID vendor "LPL", prod id 297
[    26.431] Dac detection success
[    26.431] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    26.487] (II) RADEON(0): EDID vendor "LPL", prod id 297
[    26.487] (II) RADEON(0): Printing DDC gathered Modelines:
[    26.487] (II) RADEON(0): Modeline "1280x800"x0.0   69.30  1280 1328 1360 1405  800 803 809 822 -hsync -vsync (49.3 kHz)
[    26.487] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    26.487] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    26.487] (II) RADEON(0): Manufacturer: LPL  Model: 129  Serial#: 0
[    26.487] (II) RADEON(0): Year: 2007  Week: 0
[    26.487] (II) RADEON(0): EDID Version: 1.3
[    26.487] (II) RADEON(0): Digital Display Input
[    26.487] (II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 19
[    26.487] (II) RADEON(0): Gamma: 2.20
[    26.487] (II) RADEON(0): No DPMS capabilities specified
[    26.487] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    26.487] (II) RADEON(0): First detailed timing is preferred mode
[    26.487] (II) RADEON(0): redX: 0.584 redY: 0.347   greenX: 0.324 greenY: 0.542
[    26.487] (II) RADEON(0): blueX: 0.158 blueY: 0.145   whiteX: 0.313 whiteY: 0.329
[    26.487] (II) RADEON(0): Manufacturer's mask: 0
[    26.487] (II) RADEON(0): Supported detailed timing:
[    26.487] (II) RADEON(0): clock: 69.3 MHz   Image Size:  304 x 190 mm
[    26.487] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1405 h_border: 0
[    26.487] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 822 v_border: 0
[    26.487] (II) RADEON(0):  LGPhilipsLCD
[    26.487] (II) RADEON(0):  LP141WX3-TLN1
[    26.487] (II) RADEON(0): EDID (in hex):
[    26.487] (II) RADEON(0): 	00ffffffffffff00320c290100000000
[    26.487] (II) RADEON(0): 	00110103801e13780ab3859558538a28
[    26.487] (II) RADEON(0): 	25505400000001010101010101010101
[    26.487] (II) RADEON(0): 	010101010101121b007d502016303020
[    26.487] (II) RADEON(0): 	360030be100000180000000000000000
[    26.487] (II) RADEON(0): 	00000000000000000000000000fe004c
[    26.487] (II) RADEON(0): 	475068696c6970734c43440a000000fe
[    26.487] (II) RADEON(0): 	004c503134315758332d544c4e3100b2
[    26.487] (II) RADEON(0): EDID vendor "LPL", prod id 297
[    26.509] Dac detection success
[    26.509] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    26.565] (II) RADEON(0): EDID vendor "LPL", prod id 297
[    26.565] (II) RADEON(0): Printing DDC gathered Modelines:
[    26.565] (II) RADEON(0): Modeline "1280x800"x0.0   69.30  1280 1328 1360 1405  800 803 809 822 -hsync -vsync (49.3 kHz)
[    26.565] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    26.565] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    26.565] (II) RADEON(0): Manufacturer: LPL  Model: 129  Serial#: 0
[    26.565] (II) RADEON(0): Year: 2007  Week: 0
[    26.565] (II) RADEON(0): EDID Version: 1.3
[    26.565] (II) RADEON(0): Digital Display Input
[    26.565] (II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 19
[    26.565] (II) RADEON(0): Gamma: 2.20
[    26.565] (II) RADEON(0): No DPMS capabilities specified
[    26.565] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    26.565] (II) RADEON(0): First detailed timing is preferred mode
[    26.565] (II) RADEON(0): redX: 0.584 redY: 0.347   greenX: 0.324 greenY: 0.542
[    26.565] (II) RADEON(0): blueX: 0.158 blueY: 0.145   whiteX: 0.313 whiteY: 0.329
[    26.565] (II) RADEON(0): Manufacturer's mask: 0
[    26.565] (II) RADEON(0): Supported detailed timing:
[    26.565] (II) RADEON(0): clock: 69.3 MHz   Image Size:  304 x 190 mm
[    26.565] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1405 h_border: 0
[    26.565] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 822 v_border: 0
[    26.565] (II) RADEON(0):  LGPhilipsLCD
[    26.565] (II) RADEON(0):  LP141WX3-TLN1
[    26.565] (II) RADEON(0): EDID (in hex):
[    26.565] (II) RADEON(0): 	00ffffffffffff00320c290100000000
[    26.565] (II) RADEON(0): 	00110103801e13780ab3859558538a28
[    26.565] (II) RADEON(0): 	25505400000001010101010101010101
[    26.565] (II) RADEON(0): 	010101010101121b007d502016303020
[    26.565] (II) RADEON(0): 	360030be100000180000000000000000
[    26.565] (II) RADEON(0): 	00000000000000000000000000fe004c
[    26.565] (II) RADEON(0): 	475068696c6970734c43440a000000fe
[    26.565] (II) RADEON(0): 	004c503134315758332d544c4e3100b2
[    26.565] (II) RADEON(0): EDID vendor "LPL", prod id 297
[    32.584] Dac detection success
[    32.584] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    32.640] (II) RADEON(0): EDID vendor "LPL", prod id 297
[    32.640] (II) RADEON(0): Printing DDC gathered Modelines:
[    32.640] (II) RADEON(0): Modeline "1280x800"x0.0   69.30  1280 1328 1360 1405  800 803 809 822 -hsync -vsync (49.3 kHz)
[    32.640] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    32.640] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    32.640] (II) RADEON(0): Manufacturer: LPL  Model: 129  Serial#: 0
[    32.640] (II) RADEON(0): Year: 2007  Week: 0
[    32.640] (II) RADEON(0): EDID Version: 1.3
[    32.640] (II) RADEON(0): Digital Display Input
[    32.640] (II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 19
[    32.640] (II) RADEON(0): Gamma: 2.20
[    32.640] (II) RADEON(0): No DPMS capabilities specified
[    32.640] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    32.640] (II) RADEON(0): First detailed timing is preferred mode
[    32.640] (II) RADEON(0): redX: 0.584 redY: 0.347   greenX: 0.324 greenY: 0.542
[    32.640] (II) RADEON(0): blueX: 0.158 blueY: 0.145   whiteX: 0.313 whiteY: 0.329
[    32.640] (II) RADEON(0): Manufacturer's mask: 0
[    32.640] (II) RADEON(0): Supported detailed timing:
[    32.640] (II) RADEON(0): clock: 69.3 MHz   Image Size:  304 x 190 mm
[    32.640] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1405 h_border: 0
[    32.640] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 822 v_border: 0
[    32.640] (II) RADEON(0):  LGPhilipsLCD
[    32.640] (II) RADEON(0):  LP141WX3-TLN1
[    32.640] (II) RADEON(0): EDID (in hex):
[    32.640] (II) RADEON(0): 	00ffffffffffff00320c290100000000
[    32.640] (II) RADEON(0): 	00110103801e13780ab3859558538a28
[    32.640] (II) RADEON(0): 	25505400000001010101010101010101
[    32.640] (II) RADEON(0): 	010101010101121b007d502016303020
[    32.640] (II) RADEON(0): 	360030be100000180000000000000000
[    32.641] (II) RADEON(0): 	00000000000000000000000000fe004c
[    32.641] (II) RADEON(0): 	475068696c6970734c43440a000000fe
[    32.641] (II) RADEON(0): 	004c503134315758332d544c4e3100b2
[    32.641] (II) RADEON(0): EDID vendor "LPL", prod id 297

in additional drivers it only has the broadcom for wifi. but how can it do desktop effects at all if the ati driver isn't installed? I forgot that this laptop is ati not nvidia.

I just checked ati drivers in synaptic and its installed. Why would it work sometimes and not others? makes no sense. This is just a bad version for this laptop. I have 11.04 on my desktop and it works fine.

---

### Post by Krytarik on 2011-05-18
So, I take this is an ATI Radeon X1200.

For that 'legacy' video chip, only the open source "radeon" driver (OSED) can be used, not the proprietary "fglrx" driver. The performance should nevertheless be sufficient.

Did you try to install the latter manually?

Run these commands to remove the any remnants of the "fglrx" driver and restore the functionality of the "radeon" driver:
```

sudo /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge xorg-driver-fglrx fglrx*
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri fglrx-modaliases
sudo dpkg-reconfigure xserver-xorg
```If you get error messages from the first command, post them, and don't proceed.

PS: Please edit your previous post to enclose the log in code-tags, like I described earlier, to make the thread better readable.

---

### Post by geovino on 2011-05-18
what was insstalled was done by the Ubuntu install. I just looked in synaptic and none of the fglrx components have been installed so I don't think I would need to run the commands because they are not installed.What is installed is:

xserver-xorg-video-ati
xserver-xorg-video-radeon
radeontool
xserver-xorg-video-mach64
xserver-xorg-video-r128

So what do you think is causing the on again off again desktop effects?

---

### Post by Krytarik on 2011-05-18
I was drawing my suggestion from that:
> **geovino said:**
> 
[    15.737] (II) LoadModule: "fglrx"
[    15.738] (WW) Warning, couldn't open module fglrx
[    15.738] (II) UnloadModule: "fglrx"
[    15.738] (II) Unloading fglrx
[    15.738] (EE) Failed to load module "fglrx" (module does not exist, 0)

Anyway, if no "fglrx" packages are installed, you obviously can't remove them, and if you didn't try a manual install, there is no script to run.

But you may nevertheless try reinstalling the stated packages.

You may also try upgrading the "radeon" driver through Xorg-Edgers' PPA, it offers more recent drivers than the offical repos.
Notice that this would upgrade a lot of other packages as well.
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```
If you need/want to remove those PPA and downgrade the concerning packages again:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:xorg-edgers/ppa
```

---

### Post by geovino on 2011-05-18
Thank you for all your help.

I ran:

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade

but after a shut down and reboot... still no desktop effects!
This version 11.04 isn't good for this Acer laptop. It ran better with version 10.04. I'm not going to waste anymore time tinkering with it.

---

### Post by Krytarik on 2011-05-18
> **geovino said:**
> 
This version 11.04 isn't good for this Acer laptop. It ran better with version 10.04. I'm not going to waste anymore time tinkering with it.
Ok, I'm fine with that.

---

