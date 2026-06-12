---
title: "[SOLVED] Help: Can't install nvidia driver in 8.10"
date: 2008-12-04
forum: General Help
---

### Post by 67GTA on 2008-12-04
I can not get the nvidia driver to work in Intrepid. I have never had anything like this to happen before. What I have tried:

Jockey>Envy>Manually from repos>Manually from Nvidia. I tried nvidia-xconfig after each, plus tried letting the system pick it up by it's self. All four methods have the same effect. My card is Nvidia GeForce 6150, and is supposed to be supported by the 173/177 drivers. (I have tried all four methods with both versions) After each attempt, I am greeted with the bulletproofx screen. The nv driver is used by default without an xorg.conf file. I am out of ideas. Here are two logs I saved while in recovery mode. Any ideas?

 
```
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux fastback 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Dec  4 20:10:56 2008
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

(--) PCI:*(0@0:13:0) nVidia Corporation GeForce 6150SE nForce 430 rev 162, Mem @ 0xfb000000/0, 0xd0000000/0, 0xfc000000/0, BIOS @ 0x????????/131072
(--) PCI: (0@1:5:0) Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder rev 0, Mem @ 0xe8000000/0
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [17] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [19] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
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
(II) NVIDIA GLX Module  177.80  Wed Oct  1 15:06:06 PDT 2008
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
(II) NVIDIA dlloader X Driver  177.80  Wed Oct  1 14:45:01 PDT 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00@00:0d:0
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
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [17] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [19] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
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
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:0:13:0. 
(EE) NVIDIA(0):     Please see the COMMON PROBLEMS section in the README for
(EE) NVIDIA(0):     additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```
```

5804 5586
xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe with-gdm -- /usr/bin/X :0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7 -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log


X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux fastback 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Thu Dec  4 20:10:58 2008
(++) Using config file: "/etc/X11/xorg.conf.failsafe"
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
5804 5586
cp: cannot stat `/etc/X11/xorg_conf': No such file or directory
```

---

### Post by 67GTA on 2008-12-05
I got it going after A LOT of hacking. I was troubleshooting the nvidia driver, and came across section on the Mythbuntu wiki talking about the 2.6.27 kernel and the new cx18 module(for Hauppauge 1600 TV tuner). Apparently the cx18 and nvidia binary don't play well together. I have a Hauppauge 1600... The solution was to add ```
vmalloc=192M
``` or ```
vmalloc=256M
```as a boot option depending on how much virtual memory you have. After manually chasing down the remenants of the driver from the Nvidia website and removing them, everything is running fine. The Nvidia driver was version 177.82, and Ubuntu's version was 177.80. Glxinfo was showing an API mismatch because both versions were in the system. If you are having trouble with your nvidia driver, check to see if the cx18 module is being loaded. ```
lsmod | grep cx18
```

---

### Post by kahrytan on 2008-12-08
What is 
vmalloc=256M"

---

### Post by 67GTA on 2008-12-08
Vmalloc is a library built in to the kernel to control virtual memory. The 256M is just what works best for most PC's. It basically is telling the PC to reserve the denoted amount of virtual memory. The cx18 module(still beta) is fighting with the nvidia module over virtual memory. The cx18 module gets initialized first, so the nvidia module doesn't have the resources to do it's job, and your card is not detected.

Here is a short description: [http://www.research.att.com/~gsf/download/ref/vmalloc/vmalloc.html](http://www.research.att.com/~gsf/download/ref/vmalloc/vmalloc.html)

---

### Post by kahrytan on 2008-12-09
> **67GTA said:**
> Vmalloc is a library built in to the kernel to control virtual memory. The 256M is just what works best for most PC's. It basically is telling the PC to reserve the denoted amount of virtual memory. The cx18 module(still beta) is fighting with the nvidia module over virtual memory. The cx18 module gets initialized first, so the nvidia module doesn't have the resources to do it's job, and your card is not detected.

Here is a short description: [http://www.research.att.com/~gsf/download/ref/vmalloc/vmalloc.html]("http://www.research.att.com/%7Egsf/download/ref/vmalloc/vmalloc.html")


Well, I can verify it works on my system. Should this bug be assigned to kernel driver team?

---

### Post by 67GTA on 2008-12-09
Yes it should, but I'm not sure they can fix it. At least just to get the info out there.

---

### Post by ds_pablo on 2008-12-28
I am having this same problem.  I have added the vmalloc command into my /boot/grub/menu.lst however the problem will not go away, is there somewhere else the vmalloc command needs to be added for this to work properly?  Thanks in advance

---

### Post by 67GTA on 2008-12-28
You might try changing the virtual memory amount to 192M. It depends on your hardware as to how much virtual memory you have to spread around. You might also have a separate acpi problem. Post the output of ```
dmesg
``` from a terminal if the above doesn't work.

---

### Post by Son of William on 2008-12-28
I have the following output from the "lsmod | grep cx18" command:

-----------

cx18                   96832  0 
dvb_core               86272  1 cx18
videodev               41344  2 tuner,cx18
compat_ioctl32          9344  1 cx18
i2c_algo_bit           14340  1 cx18
cx2341x                21124  1 cx18
v4l2_common            19840  4 cs5345,tuner,cx18,cx2341x
tveeprom               20228  1 cx18
i2c_core               31892  12 mxl5005s,s5h1409,tuner_simple,tda9887,tda8290,cs5345,tuner,cx18,i2c_algo_bit,v4l2_common,tveeprom,i2c_viapro

----

I assume this means I should use the vmalloc option, but where exactly?  Do I put it in menu.lst for grub?

---

### Post by 67GTA on 2008-12-28
Only if you plan to use the nvidia 3D driver. The opensource nv driver isn't affected. It should go in your /boot/grub/menu.lst. Put it anywhere at the end of the "kernel" line. Here is mine:

title        Ubuntu 8.10, kernel 2.6.27-11-generic
uuid        832bbe13-04b6-4cab-b4cc-a2af5fb8d479
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=832bbe13-04b6-4cab-b4cc-a2af5fb8d479 ro quiet splash rootflags=data=writeback vmalloc=256M acpi_osi="Linux"
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

---

### Post by Son of William on 2009-01-02
Worked like a charm.  Thanks GTA.

I had a devil of a time implementing it, however, because I had been trying to install different flavors of nvidia drivers prior to reading this thread.  

Anyone else with the same problem should make sure they have fully eradicated all other nvidia drivers from their installation first.  Then modify the grub menu.lst, and only then install the proprietary nvidia driver.

---

### Post by trainerbill on 2009-01-22
U the man... Many thanks

---

### Post by tedgoat on 2009-02-05
Thanks for the good work, 67GTA!

I'd been fiddling with this for a couple of days before stumbling upon this thread about the in compatibility of the cx18and the nvidia driver.  That's I get when I install a new card and upgrade the OS at the same time...

Now all is well, again.

---

### Post by dodongo on 2009-04-19
Phew.  Great catch -- this fix works like a charm.  Thanks, though it's been a long time since I"ve had to edit /boot/grub/menu.lst!

Am I correct in thinking that the solution for this in perpetuity is changing the following to include the vmalloc parameter?

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash **vmalloc=256M**
```

---

### Post by 67GTA on 2009-04-19
That may do the same thing. I have never tried that before. I always add boot options to the end of the kernel line. Try it out to see if it boots with that option where you have it written and let us know.

---

### Post by dodongo on 2009-04-19
> **67GTA said:**
> That may do the same thing. I have never tried that before. I always add boot options to the end of the kernel line. Try it out to see if it boots with that option where you have it written and let us know.

We'll need to wait for a new kernel to be distributed before we know for sure.  That part of the file is where the defaults for the automagically-added boot options go, but I don't believe it affects kernels that are already there.  

I *hope* that does the trick.  Will try to remember to check after a new kernel release.

---

### Post by jumping_snake on 2010-01-07
Since GRUB2 had been adopted into 9.10, here's the way to get the kernel boot command to run everytime:

Startup your system and either get to a console from the GRUB menu or boot to Ubuntu in low graphics mode and open a terminal once it's up. 

Once up, type the following command
```
sudo pico /etc/default/grub
```

Once inside of the file, search for this line

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```


right before the last ", put vmalloc=256M, so that the line looks like:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vmalloc=256M"
```

Then, hit CTRL+O and ENTER, and then CTRL+X. This will bring you back to the terminal. At this point, we need the startup system to reconfigure itself, so we type the following command

```
sudo update-grub
```

Now, reboot the system

---

