---
title: "Keyboard &amp; Mouse stopped working after update to 10.10"
date: 2010-10-12
forum: Desktop Environments
---

### Post by Charlotte18 on 2010-10-12
After I updated to 10.10, my ps/2 keyboard and mouse stopped working when in the gnome environment.

I have tried to solve this by following the instructions here:

[http://ubuntuforums.org/showthread.php?t=1504381&highlight=keyboard+mouse+-working](http://ubuntuforums.org/showthread.php?t=1504381&highlight=keyboard+mouse+-working)

. . . and by turning off usb legacy in the bios

. . . and by running these commands:
```
 sudo update-rc.d -f gdm remove
sudo update-rc.d gdm defaults 25 
```
 . . .from this web site:

[https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input)

But nothing has worked so far.

---

### Post by Charlotte18 on 2010-10-13
Now I have also tried a usb keyboard and mouse.  Still not working.

Any ideas?

---

### Post by Charlotte18 on 2010-10-13
After a couple of days of tinkering, I solved the problem by adding the following to my xorg.conf file:

```
Section "ServerFlags"
Option "AutoAddDevices" "false"
EndSection
```

I found this solution here:

[http://www.linuxquestions.org/questions/linux-newbie-8/usb-mouse-and-keyboard-not-working-after-ubuntu-8-10-upgrade-681284/](http://www.linuxquestions.org/questions/linux-newbie-8/usb-mouse-and-keyboard-not-working-after-ubuntu-8-10-upgrade-681284/)

---

### Post by Charlotte18 on 2010-10-13
Well, unfortunately, my problem is half solved.  The mouse (usb or ps/2) is working after the xorg.conf addition from my last post, but the keyboard (usb or ps/2) still does not work.

---

### Post by Charlotte18 on 2010-10-13
Well, I've also tried this, and I still don't have a working keyboard in gnome:
```
dpkg-reconfigure console-setup
```

I'm just about at wit's end. Any ideas?  Anybody?

---

### Post by avengerxp on 2010-10-13
wel it seems to be a commaon problem that occurs after upgrades, i had the same after an update on 10.04. only way to fix was re install... (being a novice, i had to take that option) :(

---

### Post by mnoyes on 2010-10-15
FWIW - I ran into keyboard trouble after updating to 10.10 on my Dell Latitude M1330. I went to system>preferences>keyboard>layouts and chose Dell Latitude from the list of keyboard models. Seems to have done the trick (I'll post again if it doesn't work...)

---

### Post by g003y on 2010-10-31
I have this problem too. I'm using a Logitech diNovo Edge keyboard. I just updated to 10.10 and when I rebooted, the mouse/keyboard was just gone.

I've also had this issue when updating to 10.04 so I had to re-install the whole damn thing. It was a painful experience so I want to know if there is another solution. I can't login without a keyboard. I can't do anything.

I think it is needless to say that it works flawlessly in Windows everytime I boot into it. However, the GRUB boot menu sometimes hang so hard that I have to restart the system if I press the arrow keys too rapidly when selecting another operating system.

---

### Post by avengerxp on 2010-11-01
Well, this seems a common problem, and has to do something with Xorg i guess (am not sure though). I wonder why it's common?

---

### Post by zuesse on 2010-11-03
OK,
I had the same problem. I went to the forums and had no real luck so here is what I did.

Over the years - been a long time with gnome - formats change from version to version. That is the case here.

.gconf is your problem. It's been in your directory for a long time and has probably survived many updates.

Well, it's time to get a new desktop anyway, so delete the .gconf directory from your home directory and...

Along with some visual changes to your desktop, your mouse and keyboard will be functioning again.

Buy the way... for those that have the synaptic touch-pads...

They suck...

---

### Post by SidF on 2010-11-09
I had a good install of 9.10 working for nearly a year and managed with some effort to get flash and wireless networking going on a 64 bit AMD machine. I tried 10.10 and immediately had mouse and keyboard problems with PS2 and USB keyboards and mice that made the install unusable. Very erratic behaviour of the mouse and and hanging at times. I uninstalled and resinstalled a few times and then tried some old mice. I found a Microsfoft serial PS2 v2 mouse that didnt have a scroll wheel and that works and there are no keyboard problems.It looks like my install can't handle a wheel mouse at all. Has anyone else found this to be the case?

---

### Post by ioargento on 2010-11-13
Same thing over here... no keyboard or synaptic mousepad on a HP Pavilion DV5-1132LA.

I'm starting to consider to upgrade only btw LTS versions... firts was the video, now this...

---

### Post by suryateja.sun on 2010-11-24
I am also getting the same problem.
Version: Ubuntu 10.10
Model: Lenovo Y500 laptop.
Keyword and Mouse is working on the second restart. Don't know whats the reason? 
Is there any update on this?

---

### Post by danteuk on 2010-12-16
Me too.
Running Kubuntu 10.10 -updated - rebooted - login screen
no keyboard or mouse working.
Re-booted and tried the all 3 kernal versions in my grub loader in normal, all boot to login with no keyboard or mouse.
Tried all in recover mode, all boot to a point and hang. No sensible messages on screen to suggest what exactly is wrong.

I'm re-installing 10.10 at the moment. If it's still f&*ked I'll be back!

PS: Machine was working just fine before the doing the updates.

---

### Post by itmanvn on 2011-05-28
Im using 11.04 gnome 3, after an update my laptop keyboard and touch not work too, If i plu usb mouse it work, please help.

---

### Post by itmanvn on 2011-05-29
Please help
> uname -a 
Linux ohmylaptop 2.6.38-8-generic-pae #42-Ubuntu SMP Mon Apr 11 05:17:09 UTC 2011 i686 i686 i386 GNU/Linux
> lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
08:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
09:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
09:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
09:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)


> lsusb 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 1a2c:0002  
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05ca:183b Ricoh Co., Ltd Visual Communication Camera VGP-VCC8 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
itmanvn@ohmylaptop:~$ lsusb 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 1a2c:0002  
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05ca:183b Ricoh Co., Ltd Visual Communication Camera VGP-VCC8 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

> [    40.954] (II) Initializing built-in extension Generic Event Extension
[    40.954] (II) Initializing built-in extension SHAPE
[    40.954] (II) Initializing built-in extension MIT-SHM
[    40.954] (II) Initializing built-in extension XInputExtension
[    40.954] (II) Initializing built-in extension XTEST
[    40.954] (II) Initializing built-in extension BIG-REQUESTS
[    40.954] (II) Initializing built-in extension SYNC
[    40.954] (II) Initializing built-in extension XKEYBOARD
[    40.954] (II) Initializing built-in extension XC-MISC
[    40.954] (II) Initializing built-in extension SECURITY
[    40.954] (II) Initializing built-in extension XINERAMA
[    40.954] (II) Initializing built-in extension XFIXES
[    40.954] (II) Initializing built-in extension RENDER
[    40.954] (II) Initializing built-in extension RANDR
[    40.954] (II) Initializing built-in extension COMPOSITE
[    40.954] (II) Initializing built-in extension DAMAGE
[    40.954] (II) Initializing built-in extension GESTURE
[    40.970] (II) AIGLX: Trying DRI driver /usr/lib/dri/i965_dri.so
[    41.010] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    41.010] (II) AIGLX: enabled GLX_INTEL_swap_event
[    41.010] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    41.010] (II) AIGLX: enabled GLX_SGI_make_current_read
[    41.010] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    41.010] (II) AIGLX: Loaded and initialized i965
[    41.010] (II) GLX: Initialized DRI2 GL provider for screen 0
[    41.011] (II) intel(0): Setting screen physical size to 338 x 211
[    41.029] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    41.032] (II) Using input driver 'synaptics' for 'Synaptics Touchpad'
[    41.032] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    41.032] (**) Option "SendCoreEvents" "true"
[    41.032] (**) Synaptics Touchpad: always reports core events
[    41.032] (**) Option "Device" "/dev/psaux"
[    41.032] (--) Synaptics Touchpad: invalid x-axis range.  defaulting to 1615 - 5685
[    41.032] (--) Synaptics Touchpad: invalid y-axis range.  defaulting to 1729 - 4171
[    41.032] (--) Synaptics Touchpad: invalid pressure range.  defaulting to 0 - 256
[    41.032] (--) Synaptics Touchpad: invalid finger width range.  defaulting to 0 - 16
[    41.032] (**) Option "HorizEdgeScroll" "0"
[    41.052] (EE) Query no Synaptics: 6003C8
[    41.052] (--) Synaptics Touchpad: no supported touchpad found
[    41.052] (EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
[    41.056] (EE) PreInit returned 11 for "Synaptics Touchpad"
[    41.056] (II) UnloadModule: "synaptics"
[    41.056] (II) Unloading synaptics
[    66.333] (II) config/udev: Adding input device USB USB Keykoard (/dev/input/event11)
[    66.333] (**) USB USB Keykoard: Applying InputClass "evdev keyboard catchall"
[    66.333] (II) LoadModule: "evdev"
[    66.333] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    66.333] (II) Module evdev: vendor="X.Org Foundation"
[    66.333] 	compiled for 1.10.0.902, module version = 2.6.0
[    66.333] 	Module class: X.Org XInput Driver
[    66.334] 	ABI class: X.Org XInput driver, version 12.3
[    66.334] (II) Using input driver 'evdev' for 'USB USB Keykoard'
[    66.334] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    66.334] (**) USB USB Keykoard: always reports core events
[    66.334] (**) USB USB Keykoard: Device: "/dev/input/event11"
[    66.348] (--) USB USB Keykoard: Found 1 mouse buttons
[    66.348] (--) USB USB Keykoard: Found scroll wheel(s)
[    66.348] (--) USB USB Keykoard: Found relative axes
[    66.348] (--) USB USB Keykoard: Found absolute axes
[    66.348] (II) evdev-grail: failed to open grail, no gesture support
[    66.348] (--) USB USB Keykoard: Found keys
[    66.348] (II) USB USB Keykoard: Configuring as mouse
[    66.348] (II) USB USB Keykoard: Configuring as keyboard
[    66.348] (II) USB USB Keykoard: Adding scrollwheel support
[    66.348] (**) USB USB Keykoard: YAxisMapping: buttons 4 and 5
[    66.348] (**) USB USB Keykoard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    66.348] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.1/input/input11/event11"
[    66.348] (II) XINPUT: Adding extended input device "USB USB Keykoard" (type: KEYBOARD)
[    66.348] (**) Option "xkb_rules" "evdev"
[    66.348] (**) Option "xkb_model" "pc105"
[    66.348] (**) Option "xkb_layout" "us"
[    66.349] (EE) USB USB Keykoard: failed to initialize for relative axes.
[    66.349] (II) USB USB Keykoard: initialized for absolute axes.
[    66.349] (**) USB USB Keykoard: (accel) keeping acceleration scheme 1
[    66.349] (**) USB USB Keykoard: (accel) acceleration profile 0
[    66.349] (**) USB USB Keykoard: (accel) acceleration factor: 2.000
[    66.349] (**) USB USB Keykoard: (accel) acceleration threshold: 4
[    66.350] (II) config/udev: Adding input device USB USB Keykoard (/dev/input/event10)
[    66.350] (**) USB USB Keykoard: Applying InputClass "evdev keyboard catchall"
[    66.350] (II) Using input driver 'evdev' for 'USB USB Keykoard'
[    66.350] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    66.350] (**) USB USB Keykoard: always reports core events
[    66.350] (**) USB USB Keykoard: Device: "/dev/input/event10"
[    66.360] (--) USB USB Keykoard: Found keys
[    66.360] (II) USB USB Keykoard: Configuring as keyboard
[    66.360] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input10/event10"
[    66.360] (II) XINPUT: Adding extended input device "USB USB Keykoard" (type: KEYBOARD)
[    66.360] (**) Option "xkb_rules" "evdev"
[    66.360] (**) Option "xkb_model" "pc105"
[    66.360] (**) Option "xkb_layout" "us"
[    66.381] (II) config/udev: Adding input device Genius       Optical Mouse (/dev/input/event12)
[    66.381] (**) Genius       Optical Mouse: Applying InputClass "evdev pointer catchall"
[    66.381] (II) Using input driver 'evdev' for 'Genius       Optical Mouse'
[    66.381] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    66.381] (**) Genius       Optical Mouse: always reports core events
[    66.381] (**) Genius       Optical Mouse: Device: "/dev/input/event12"
[    66.396] (--) Genius       Optical Mouse: Found 3 mouse buttons
[    66.396] (--) Genius       Optical Mouse: Found scroll wheel(s)
[    66.396] (--) Genius       Optical Mouse: Found relative axes
[    66.396] (--) Genius       Optical Mouse: Found x and y relative axes
[    66.396] (II) Genius       Optical Mouse: Configuring as mouse
[    66.396] (II) Genius       Optical Mouse: Adding scrollwheel support
[    66.396] (**) Genius       Optical Mouse: YAxisMapping: buttons 4 and 5
[    66.396] (**) Genius       Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    66.396] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input12/event12"
[    66.396] (II) XINPUT: Adding extended input device "Genius       Optical Mouse" (type: MOUSE)
[    66.396] (II) Genius       Optical Mouse: initialized for relative axes.
[    66.396] (**) Genius       Optical Mouse: (accel) keeping acceleration scheme 1
[    66.396] (**) Genius       Optical Mouse: (accel) acceleration profile 0
[    66.396] (**) Genius       Optical Mouse: (accel) acceleration factor: 2.000
[    66.396] (**) Genius       Optical Mouse: (accel) acceleration threshold: 4
[    66.397] (II) config/udev: Adding input device Genius       Optical Mouse (/dev/input/mouse3)
[    66.397] (II) No input driver/identifier specified (ignoring)
[   159.387] (II) XKB: reuse xkmfile /var/lib/xkb/server-81EC4871279DB1D73113D19E789F270C19322F52.xkm
[   848.681] (II) AIGLX: Suspending AIGLX clients for VT switch
[   852.368] (II) Open ACPI successful (/var/run/acpid.socket)
[   852.368] (II) AIGLX: Resuming AIGLX clients after VT switch
[   872.839] (II) XKB: reuse xkmfile /var/lib/xkb/server-81EC4871279DB1D73113D19E789F270C19322F52.xkm
[  9215.912] (II) config/udev: removing device USB USB Keykoard
[  9215.912] (II) USB USB Keykoard: Close
[  9215.912] (II) UnloadModule: "evdev"
[  9215.912] (II) Unloading evdev
[  9215.940] (II) config/udev: removing device USB USB Keykoard
[  9215.940] (II) USB USB Keykoard: Close
[  9215.940] (II) UnloadModule: "evdev"
[  9215.940] (II) Unloading evdev
[  9217.103] (II) config/udev: Adding input device USB USB Keykoard (/dev/input/event10)
[  9217.103] (**) USB USB Keykoard: Applying InputClass "evdev keyboard catchall"
[  9217.103] (II) Using input driver 'evdev' for 'USB USB Keykoard'
[  9217.103] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  9217.103] (**) USB USB Keykoard: always reports core events
[  9217.103] (**) USB USB Keykoard: Device: "/dev/input/event10"
[  9217.112] (--) USB USB Keykoard: Found keys
[  9217.112] (II) USB USB Keykoard: Configuring as keyboard
[  9217.112] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input13/event10"
[  9217.112] (II) XINPUT: Adding extended input device "USB USB Keykoard" (type: KEYBOARD)
[  9217.112] (**) Option "xkb_rules" "evdev"
[  9217.112] (**) Option "xkb_model" "pc105"
[  9217.112] (**) Option "xkb_layout" "us"
[  9227.112] (II) config/udev: Adding input device USB USB Keykoard (/dev/input/event11)
[  9227.112] (**) USB USB Keykoard: Applying InputClass "evdev keyboard catchall"
[  9227.112] (II) Using input driver 'evdev' for 'USB USB Keykoard'
[  9227.112] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  9227.112] (**) USB USB Keykoard: always reports core events
[  9227.112] (**) USB USB Keykoard: Device: "/dev/input/event11"
[  9227.128] (--) USB USB Keykoard: Found 1 mouse buttons
[  9227.128] (--) USB USB Keykoard: Found scroll wheel(s)
[  9227.128] (--) USB USB Keykoard: Found relative axes
[  9227.128] (--) USB USB Keykoard: Found absolute axes
[  9227.128] (II) evdev-grail: failed to open grail, no gesture support
[  9227.128] (--) USB USB Keykoard: Found keys
[  9227.128] (II) USB USB Keykoard: Configuring as mouse
[  9227.128] (II) USB USB Keykoard: Configuring as keyboard
[  9227.128] (II) USB USB Keykoard: Adding scrollwheel support
[  9227.128] (**) USB USB Keykoard: YAxisMapping: buttons 4 and 5
[  9227.128] (**) USB USB Keykoard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  9227.128] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.1/input/input14/event11"
[  9227.128] (II) XINPUT: Adding extended input device "USB USB Keykoard" (type: KEYBOARD)
[  9227.128] (**) Option "xkb_rules" "evdev"
[  9227.128] (**) Option "xkb_model" "pc105"
[  9227.128] (**) Option "xkb_layout" "us"
[  9227.129] (EE) USB USB Keykoard: failed to initialize for relative axes.
[  9227.129] (II) USB USB Keykoard: initialized for absolute axes.
[  9227.129] (**) USB USB Keykoard: (accel) keeping acceleration scheme 1
[  9227.129] (**) USB USB Keykoard: (accel) acceleration profile 0
[  9227.129] (**) USB USB Keykoard: (accel) acceleration factor: 2.000
[  9227.129] (**) USB USB Keykoard: (accel) acceleration threshold: 4
> /etc/X11/xorg.conf
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

# commented out by update-manager, HAL is now used
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

# commented out by update-manager, HAL is now used
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

# commented out by update-manager, HAL is now used
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
# commented out by update-manager, HAL is now used
	InputDevice	"Synaptics Touchpad"
EndSection


---

### Post by itmanvn on 2011-06-23
bump, still not fixed!

---

