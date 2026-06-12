---
title: "Gnome does not start correctly after update"
date: 2010-12-04
forum: Desktop Environments
---

### Post by Messyhair42 on 2010-12-04
I recently got the last round of updates, including linux kernel 2.6.32.26. after several programs froze up (i hadn't restarted since the update) i restarted only to find that Gnome starts up into a different look than I had it setup to (normally with a custom theme and without a login prompt). it now starts with a more basic theme and a login prompt which won't accept my password. something similar had happened before and i fixed it by booting into recovery mode and running dpkg, and having to reboot more than once but it returned to normal. I tried running it again and it hasn't worked, so I must ask for advice. I am working from Fedora 10 on the same computer. Thank you for any assistance you might be able to provide

---

### Post by Messyhair42 on 2010-12-05
after another cycle of rebooting in an attempt to fix the problem (i moved to where i could get a hardwired internet connection) it now drops direclty to the shell when i try to boot into ubuntu from grub

is there a way to just reinstall Gnome from either shell or live cd?

---

### Post by 3Miro on 2010-12-05
Which Ubuntu is this and is it netbook or desktop edition?

If I understand correctly, you have a dual-boot with Ubuntu and Fedora 10. Which version of Grub are you using, the one from Ubuntu or the one form Fedora? Do you get Grub entries for an older kernel?

What is your video card?

(Gnome not starting means that Xorg is not starting, which means that you have an issue with the video drivers)

---

### Post by Messyhair42 on 2010-12-05
I have ubuntu 10.04 desktop. Grub 1.98 boots from my primary master drive with Ubuntu (/dev/sdb), Fedora also has it's own instance of Grub, but it's on a separate hard drive. grub displays entries for the five most recent kernels 2.6.32.22-.26. I have been sticking with running 2.6.43.23 because under the newer kernels I was having problems with compiz. my video card is a GeForce 7200 GS, and ever since I have been running ubuntu i've used the proprietary drivers.

---

### Post by 3Miro on 2010-12-05
Most likely, the Nvidia driver does not work properly wit the new kernel. This is a problem with Nvidia sometimes, they have their own proprietary driver and every time you update the kernel, you have to recompile the Nvidia module (as opposed to including it by default), this should be done automatically, but naturally it sometimes fails.

The easiest way to fix this is to try any version of the kernel that gives you a graphical environment (don't bother with compiz yet). Then go to System -> Admin -> Hardware Drivers, uninstall the Nvidia driver, reboot, then install the driver again (then reboot). Hopefully this will fix the problem.

---

### Post by Messyhair42 on 2010-12-05
I have tried different kernel versions already, and I was getting the ubuntu spash screen, and then a very basic looking desktop with a login prompt. the prompt won't accept my user password so i can't even get into the system with a gui.
If there is a way to use the command shell to do the same things (at least deactivate the driver) assistance would be appriciated

---

### Post by 3Miro on 2010-12-05
```
 sudo dpkg-reconfigure xserver-xorg 
```

This should disable the Nvidia driver. There is nothing in the official Ubuntu HowTo that mentions how to fix the Nvidia driver without a gui, so hopefully this will help.

---

### Post by Messyhair42 on 2010-12-06
> **3Miro said:**
> ```
 sudo dpkg-reconfigure xserver-xorg 
```

This should disable the Nvidia driver. There is nothing in the official Ubuntu HowTo that mentions how to fix the Nvidia driver without a gui, so hopefully this will help.

the command didn't let me login, whether it disabled the driver or not i'm not sure.
I'm thinking the problem had something to do with the last round of updates i downloaded not being configured right or actually have an error in them.
I could pull the video card and run straight from the motherboard, but I have my doubts that that would fix the problem.
I think I need to do something to the Gnome installation/files. or use the netroot option to install KDE and work from there. all just ideas I'm coming up with on the fly. thanks for your assistance, but this is really bugging me.

---

### Post by 3Miro on 2010-12-06
What is actually happening. Do you get the graphical login screen or just a command line login. If you get the graphical one then the driver issue should be fixed for now (you will still have to reinstall the driver later, but things will be working for now). If you cannot login from the graphical screen, then you probably have messed up Gnome setup. If you are comfortable with the command line, you can hit Ctr + Alt + F1 to go into CLI mode again (Ctr + Alt + F7 gets you back) can you can look into your home folder for .gnome and .gconf files. Then delete them. 

You can also do that from a LiveCD (you should always keep one handy for situations like this). From the LiveCD you can open Nautilus and use Ctr + H to see the hidden files that start with .something.

A third way to do this is to install another graphical environment like you suggest. However, if you only want to login to fix your files, you should probably install xfce4 and not KDE, since KDE is somewhat big. You can use the command:
```
 sudo apt-get install xfce4 
```
You can also use xubuntu-desktop, but this will pull more files and change some settings.

---

### Post by Swiftjay on 2010-12-06
I keep a driver of my nvidia graphics card just for this sole reason I have to go into the recovery console and run the graphics card drive via terminal from there.

sh /home/USER/graphicscardname.xx  this will run the graphics card install in terminal and re-compile it.  It's annoying but..hey it's gotta be done.

If you need to get into recovery console press shift at the begining of the screen to get in, which I only just learnt now how to do so, lol.

---

### Post by Messyhair42 on 2010-12-06
@3miro. I was getting the login screen until about a day ago, now I get the Ubuntu splash screen and then the CLI login. I was planning on using a liveCD to poke around /. I'd prefer not to have to install xfce if i can avoid it.
@Swiftjay. If I can get the graphics driver from say a thumb drive with ubuntu on it can i use it to replace the driver on my desktop insallation through CLI?

---

### Post by 3Miro on 2010-12-06
If you cannot get to the login screen, then the problem is not with Gnome, but with the driver. You should try to uninstall anything nvidia first, then try to reconfigure xorg again.

Look at the errors that you get from:
```
startx
```
and
```
 sudo service gdm start 
```
or
```
 sudo /etc/init.d/gdm start 
```

It will probably be something about the driver.

```
aptitude search nvidia
```
should list packages for Nvidia or
```
aptitude search nvidia | less 
```
if the list is too long.
Then you can use
```
 sudo apt-get purge somethin-nvidia-something 
```
to uninstall them. Then reconfigure should work, but I am not sure. At this point complete reinstall of the OS might be the only viable option.

---

### Post by Messyhair42 on 2010-12-07
```
startx
```
yielded
Fatal error:no screens found
```
sudo service gdm start
```
yielded
gdm/running
i didn't try the last one b/c i cant get internet access without moving my box

if it comes to a reinstallation (never done one (partial) before, not too opposed to it)...I have /, /tmp /var, /home, and /usr on separate partitions (logical). can I only reinstall / and leave /home alone? it would take some work, and an extra storage device (which is in the mail right now) and a flash drive installation but it wouldn't be too hard to rebuild, but fixing it is preferable.

---

### Post by 3Miro on 2010-12-07
There has to be more about the startx error, something about nvidia kernel module or something like that. The log is stored in /var/logs/Xorg.0.log, it would be nice to look at it.

If you make a reinstall, then you don't have to format /home and /tmp, but I would recommend formating /var and /usr. For home, it is also safer to use the liveCD to rename the home folder to something like your_username_backup and start with a clean /home folder. Then you can move your files from your_username_backup to your_username. That way you will be able to overwrite all the .something settings.

---

### Post by Messyhair42 on 2010-12-07
had some trouble finding it through Fedora but here is /var/log/Xorg.0.log
```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
Current Operating System: Linux deepthought 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 09:00:03 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-26-generic root=UUID=daba79c9-1e85-4e65-bfbf-aec5551b1217 ro single
Build Date: 10 November 2010  11:25:26AM
xorg-server 2:1.7.6-2ubuntu7.4 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec  7 06:29:14 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f1b20
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 2

(--) PCI:*(0:1:0:0) 10de:01d3:0000:0483 nVidia Corporation G72 [GeForce 7300 SE/7200 GS] rev 161, Mem @ 0xd1000000/16777216, 0xc0000000/268435456, 0xd0000000/16777216, BIOS @ 0x????????/131072
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 10:38:29 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched nouveau as autoconfigured driver 0
(==) Matched nv as autoconfigured driver 1
(==) Matched vesa as autoconfigured driver 2
(==) Matched fbdev as autoconfigured driver 3
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "nouveau"
(II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
(II) Module nouveau: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.15
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.7.3.901, module version = 2.1.15
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.4.1
	ABI class: X.Org Video Driver, version 6.0
(II) NOUVEAU driver Date:   Wed Feb 10 18:43:39 2010 +0100
(II) NOUVEAU driver for NVIDIA chipset families :
	RIVA TNT    (NV04)
	RIVA TNT2   (NV05)
	GeForce 256 (NV10)
	GeForce 2   (NV11, NV15)
	GeForce 4MX (NV17, NV18)
	GeForce 3   (NV20)
	GeForce 4Ti (NV25, NV28)
	GeForce FX  (NV3x)
	GeForce 6   (NV4x)
	GeForce 7   (G7x)
	GeForce 8   (G8x)
(II) NOUVEAU driver Date:   Wed Feb 10 18:43:39 2010 +0100
(II) NOUVEAU driver for NVIDIA chipset families :
	RIVA TNT    (NV04)
	RIVA TNT2   (NV05)
	GeForce 256 (NV10)
	GeForce 2   (NV11, NV15)
	GeForce 4MX (NV17, NV18)
	GeForce 3   (NV20)
	GeForce 4Ti (NV25, NV28)
	GeForce FX  (NV3x)
	GeForce 6   (NV4x)
	GeForce 7   (G7x)
	GeForce 8   (G8x)
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:00:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card1
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card2
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card3
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card4
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card5
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card6
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card7
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card8
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card9
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card10
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card11
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card12
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card13
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card14
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card15
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: node name is /dev/dri/card15
(EE) [drm] failed to open device
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Video Driver, version 6.0
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 262144 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 5.114
(II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
(II) VESA(0): VESA VBE OEM Product: G72 Board - c1018u  
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
(II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level none
(II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
(II) VESA(0): VESA VBE DDC read failed
(II) VESA(0): VESA VBE PanelID read successfully
(II) VESA(0): PanelID returned panel resolution 0x0
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 100 (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009507
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 101 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009507
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 10
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 10
	LinNumberOfImagePages: 10
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 102 (800x600)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009507
	BytesPerScanline: 100
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 100
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 103 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009507
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 800
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 104 (1024x768)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009507
	BytesPerScanline: 128
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 128
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 105 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009507
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 10e (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009507
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 10f (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009507
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 111 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009507
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 112 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009507
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 114 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009507
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 115 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009507
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 117 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009507
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 118 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009507
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 130 (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009507
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 62
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 62
	LinNumberOfImagePages: 62
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 131 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009507
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 132 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009507
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 133 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009507
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 134 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009507
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 135 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009507
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 19
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 19
	LinNumberOfImagePages: 19
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 136 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009507
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 10
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 10
	LinNumberOfImagePages: 10
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 13d (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009507
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 13e (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009507
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000

(II) VESA(0): Total Memory: 4096 64KB banks (262144kB)
(II) VESA(0): <default monitor>: Using hsync range of 31.50-0.00 kHz
(II) VESA(0): <default monitor>: Using vrefresh range of 56.00-0.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
(WW) VESA(0): No valid modes left. Trying less strict filter...
(II) VESA(0): <default monitor>: Using hsync range of 31.50-0.00 kHz
(II) VESA(0): <default monitor>: Using vrefresh range of 56.00-0.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1024x768" (unknown reason)
(II) VESA(0): Not using built-in mode "800x600" (unknown reason)
(II) VESA(0): Not using built-in mode "640x480" (unknown reason)
(II) VESA(0): Not using built-in mode "640x400" (unknown reason)
(II) VESA(0): Not using built-in mode "320x400" (unknown reason)
(II) VESA(0): Not using built-in mode "320x240" (unknown reason)
(II) VESA(0): Not using built-in mode "320x200" (unknown reason)
(WW) VESA(0): No valid modes left. Trying aggressive sync range...
(II) VESA(0): <default monitor>: Using hsync range of 31.50-0.00 kHz
(II) VESA(0): <default monitor>: Using vrefresh range of 50.00-0.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1024x768" (unknown reason)
(II) VESA(0): Not using built-in mode "800x600" (unknown reason)
(II) VESA(0): Not using built-in mode "640x480" (unknown reason)
(II) VESA(0): Not using built-in mode "640x400" (unknown reason)
(II) VESA(0): Not using built-in mode "320x400" (unknown reason)
(II) VESA(0): Not using built-in mode "320x240" (unknown reason)
(II) VESA(0): Not using built-in mode "320x200" (unknown reason)
(EE) VESA(0): No valid modes
(II) UnloadModule: "vesa"
(II) UnloadModule: "int10"
(II) Unloading /usr/lib/xorg/modules/libint10.so
(II) UnloadModule: "vbe"
(II) Unloading /usr/lib/xorg/modules/libvbe.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```

---

### Post by 3Miro on 2010-12-07
OK, so the thing is trying to use the generic VESA driver (like we wanted, you will reinstall Nvidia once you get VESA working). However, VESA doesn't recognize the monitor:

```
 (EE) VESA(0): No valid modes 
```
You can Google the error and several things come up. Apparently you will have to manually edit your xorg configuration. The files are
```
 /etc/X11/xorg.conf
/etc/X11/xorg.conf.d/

```
(the last one is a folder, if no xorg.conf file exists, the files in xorg.conf.d will get combined together to make an xorg.conf). You have to find the monitor settings and try to add a mode or refresh rate. Look here:

[http://www.linuxquestions.org/questions/red-hat-31/intel-gma-x3100-vesa-no-valid-modes-658394/](http://www.linuxquestions.org/questions/red-hat-31/intel-gma-x3100-vesa-no-valid-modes-658394/)

[https://bugs.launchpad.net/xorg-server/+bug/89853](https://bugs.launchpad.net/xorg-server/+bug/89853)

(second one is more relevant)

---

### Post by Messyhair42 on 2010-12-07
thank you for your help and patience. I'm going to start a new thread to be more specific now that I know what the problem is.

---

