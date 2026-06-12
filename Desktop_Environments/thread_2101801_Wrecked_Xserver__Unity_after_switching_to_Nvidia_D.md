---
title: "Wrecked Xserver / Unity after switching to Nvidia Drivers [12.04]"
date: 2013-01-05
forum: Desktop Environments
---

### Post by hulp on 2013-01-05
Hi everybody,

I used the default Ubuntu video drivers until recently (Nouveau, I think) and wanted to change to a proprietary Nvideau driver (Nvidia_current for my GeForce 8800 GTX). I had problems with that before... earlier Ubuntu installation (also 12.04) would just lag and bug and do almost nothing after logging in. Switching to 2D desktop mode back then did the trick, at least I could access the driver settings again using the GUI.

EDIT: Situation has changed a bit, and for better structure, here in short:
I solved the driver problem, but I am not any longer able to login with my Ubuntu Account using lightdm. Guest account works. Obviously several people had this problem after turning off the login sound, but I didn't change any of the settings. One solution that has been proposed didn't work for me. Switching to gdm works fine, using it as a temporary solution. 

I'd especially ask you to
a) Tell me if my xorg.conf should look different, because I don't know if it's the original one or has been overwritten by the nvidia configuration
b) If someone can make sense of the lightdm error logs

(EE) and (WW) from xorg.o.conf:
```
     (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    37.111] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    37.111] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    37.111] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    37.111] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    37.111] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    37.111] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    37.112] (II) Loading extension MIT-SCREEN-SAVER
[    37.114] (WW) Warning, couldn't open module nvidia
[    37.114] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    37.115] (WW) Warning, couldn't open module nv
[    37.115] (EE) Failed to load module "nv" (module does not exist, 0)
[    37.116] (WW) Warning, couldn't open module nvidia
[    37.116] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    37.116] (WW) Warning, couldn't open module nv
[    37.116] (EE) Failed to load module "nv" (module does not exist, 0)
[    37.118] (WW) Falling back to old probe method for vesa
[    37.118] (WW) Falling back to old probe method for fbdev
[    37.553] (WW) NOUVEAU(0): Option "NoLogo" is not used
[    37.599] (WW) evdev: Logitech Unifying Device. Wireless PID:2007: ignoring absolute axes.
[    37.601] (WW) evdev: Logitech Unifying Device. Wireless PID:2007: ignoring absolute axes.
```

x-0-greeter.log from lightdm (user login and guest login, the second one works)
```
[+0.00s] DEBUG: unity-greeter.vala:850: Starting unity-greeter 0.2.8 UID=104 LANG=en_GB.UTF-8
[+0.00s] DEBUG: unity-greeter.vala:853: Setting cursor
[+0.00s] DEBUG: unity-greeter.vala:857: Creating background surface
[+0.00s] DEBUG: unity-greeter.vala:860: Loading command line options
[+0.00s] DEBUG: unity-greeter.vala:888: Setting GTK+ settings
Activating service name='org.a11y.atspi.Registry'
Successfully activated service 'org.a11y.atspi.Registry'

** (at-spi2-registryd:2934): WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (at-spi2-registryd:2934): WARNING **: Unable to register client with session manager
[+0.03s] DEBUG: unity-greeter.vala:911: Creating Unity Greeter
[+0.03s] DEBUG: Connecting to display manager...
[+0.03s] DEBUG: Wrote 17 bytes to daemon
[+0.03s] DEBUG: Read 8 bytes from daemon
[+0.03s] DEBUG: Read 120 bytes from daemon
[+0.03s] DEBUG: Connected version=1.2.1 default-session=ubuntu show-manual-login=false hide-users=false has-guest-account=true
[+0.09s] DEBUG: menubar.vala:318: LANG=en_GB.UTF-8 LANGUAGE=en_GB:en
[+0.10s] CRITICAL: g_error_free: assertion `error != NULL' failed
[+0.10s] DEBUG: get entries
[+0.10s] DEBUG: menubar.vala:511: Adding indicator object 0x176f078 at position 0
[+0.11s] DEBUG: Evaluating bitmask for '%H:%M'
[+0.11s] DEBUG: Checking against 1 possible times
[+0.11s] DEBUG: Guessing max time width: 36
[+0.11s] DEBUG: get entries
[+0.11s] DEBUG: menubar.vala:511: Adding indicator object 0x17e5188 at position 1
[+0.11s] WARNING: IndicatorObject class does not have an accessible description.
[+0.12s] WARNING: IndicatorObject class does not have an accessible description.
[+0.12s] DEBUG: get entries
[+0.12s] DEBUG: get entries
[+0.12s] DEBUG: menubar.vala:511: Adding indicator object 0x185f058 at position 2
[+0.12s] DEBUG: menubar.vala:335: LANG=en_GB.UTF-8 LANGUAGE=en_GB:en
[+0.12s] DEBUG: Loaded session /usr/share/xsessions/ubuntu-2d.desktop (Ubuntu 2D, This session logs you into Ubuntu 2D Mode)
[+0.12s] DEBUG: Loaded session /usr/share/xsessions/xterm.desktop (Recovery Console, Failsafe session with only xterm)
[+0.12s] DEBUG: Ignoring session /usr/share/xsessions/gnome.desktop
[+0.12s] DEBUG: Loaded session /usr/share/xsessions/ubuntu.desktop (Ubuntu, This session logs you into Ubuntu)
[+0.12s] DEBUG: Ignoring session /usr/share/xsessions/gnome-shell.desktop
[+0.12s] DEBUG: Loaded session /usr/share/xsessions/xsession.desktop (User Defined Session, Custom ~/.xsession script)
[+0.12s] DEBUG: session-chooser.vala:42: Adding session xterm (Recovery Console)
[+0.12s] DEBUG: session-chooser.vala:42: Adding session ubuntu (Ubuntu)
[+0.13s] DEBUG: session-chooser.vala:42: Adding session ubuntu-2d (Ubuntu 2D)
[+0.13s] DEBUG: session-chooser.vala:42: Adding session xsession (User Defined Session)
[+0.52s] DEBUG: Setting keyboard layout to 'de'
[+0.79s] DEBUG: main-window.vala:98: Screen is 1920x1080 pixels
[+0.79s] DEBUG: main-window.vala:104: Monitor 0 is 1920x1080 pixels at 0,0
[+0.79s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.79s] DEBUG: Loading user /org/freedesktop/Accounts/User1000
[+0.80s] DEBUG: Loading sessions from org.freedesktop.DisplayManager
[+0.80s] DEBUG: unity-greeter.vala:327: Adding/updating user m**** (name)
[+0.80s] DEBUG: unity-greeter.vala:184: Adding guest account entry

**[+0.80s] DEBUG: Starting authentication for user m******...**

[+0.80s] DEBUG: Wrote 25 bytes to daemon
[+0.80s] DEBUG: unity-greeter.vala:914: Showing greeter
[+0.80s] DEBUG: unity-greeter.vala:352: Showing main window
[+0.80s] DEBUG: New style for time label
[+0.81s] DEBUG: Evaluating bitmask for '%H:%M'
[+0.81s] DEBUG: Checking against 1 possible times
[+0.81s] DEBUG: Guessing max time width: 36
[+0.82s] DEBUG: background.vala:315: Regenerating backgrounds
[+0.82s] DEBUG: background.vala:67: Making background /usr/share/backgrounds/warty-final-ubuntu.png at 1920x1080
[+0.82s] DEBUG: New style for time label
[+0.82s] DEBUG: Evaluating bitmask for '%H:%M'
[+0.82s] DEBUG: Checking against 1 possible times
[+0.82s] DEBUG: Guessing max time width: 36
[+0.82s] DEBUG: unity-greeter.vala:927: Starting main loop
[+0.82s] DEBUG: Read 8 bytes from daemon
[+0.82s] DEBUG: Read 39 bytes from daemon
[+0.82s] DEBUG: Prompt user with 1 message(s)
**[+0.86s] WARNING: Getting layout failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `com.canonical.dbusmenu' on object at path /com/canonical/indicator/users/menu**
[+0.86s] DEBUG: notify visible signal received
[+0.86s] CRITICAL: ido_calendar_menu_item_set_date: assertion `IDO_IS_CALENDAR_MENU_ITEM(menuitem)' failed
[+0.86s] DEBUG: Num devices: '0'

[+0.86s] MESSAGE: Couldn't find primary device
[+0.86s] DEBUG: Num devices: '0'

[+0.86s] DEBUG: icon_policy is: 0 (present==0, charge==1, never==2)
[+0.86s] DEBUG: count_batteries found 0 batteries (0 are charging/discharging)
[+0.86s] DEBUG: should_be_visible: no
[+0.86s] DEBUG: menubar.vala:519: Removing indicator object 0x16ca658
[+0.86s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+0.86s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+0.86s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+0.86s] WARNING: menubar.vala:531: Indicator object 0x16ca658 not in menubar
[+0.87s] DEBUG: New calendar item
[+0.87s] DEBUG: unity-greeter.vala:310: starting system-ready sound
[+0.89s] DEBUG: indicator-sound: new_volume_slider_widget
[+0.90s] DEBUG: indicator-sound: new_voip_slider_widget
[+0.90s] DEBUG: background.vala:116: Render of background /usr/share/backgrounds/warty-final-ubuntu.png complete
[+1.02s] DEBUG: background.vala:67: Making background /home/m*****/Pictures/Wallpaper/ubuntu-silver-blue1440x900_0.jpg at 1920x1080
[+1.06s] DEBUG: background.vala:116: Render of background /home/m****/Pictures/Wallpaper/ubuntu-silver-blue1440x900_0.jpg complete
[+1.18s] DEBUG: Setting keyboard layout to 'de'
[+115.47s] DEBUG: Starting authentication for guest account...
[+115.47s] DEBUG: Wrote 12 bytes to daemon
[+115.47s] DEBUG: Read 8 bytes from daemon
[+115.47s] DEBUG: Read 12 bytes from daemon
[+115.47s] DEBUG: Authentication complete for user  with return code 0
[+115.84s] DEBUG: Setting keyboard layout to 'de'
[+116.50s] DEBUG: user-list.vala:558: Start session for *guest
[+116.51s] DEBUG: Starting default session
[+116.51s] DEBUG: Wrote 12 bytes to daemon
[+116.51s] DEBUG: Read 8 bytes from daemon
[+116.51s] DEBUG: Read 4 bytes from daemon 
```




=====================================================================================================
Old Part:
=====================================================================================================

This time, however, it didn't. It wasn't possible to do anything after logging in any more (login screen and everything before behaved normally). In a first attempt I tried to add the line driver "Nouveau" to xorg.conf, but that didn't help. Removed it again. Tried to switch drivers using jockey-text, but you only have the choice between Nvidia drivers. I gave them a shot, tried different versions, still no success. I made  a backup of the xorg.conf and and used the failsafe version instead. Also tried to boot into backup / recovery mode once, but if I remember correctly Ubuntu complained about not being able to unlock my luks partitions (fully encrypted + LVM). 

Also, at a certain point I wouldn't even be able to login any more. You entered your user information, tried to login, but Ubuntu would remain at the login screen. Later Login Screen / Xserver wouldn't start anymore... trying to start it manually, log complained about "no screens found". Unfortunately I cannot provide you with information what actions of mine impaired the situation. 

I suspect that my hasty and not very deliberate attempts to fix all this just had the opposite effect. Although I only tried to change the xorg.conf and using jockey-text.
Somehow my 8800 GTX is refusing to collaborate with Ubuntu every since ... 

It would be great if somebody could point me into the right direction. Thanks already.
If you require any error logs / files, let me now.

Best regards
hulp

EDIT2: I apparently successfully fixed the mess with my drivers. I simply purged all nvidia drivers. 
Back to the original problem where the login screen loads, but just jumps back after giving the password. Interestingly I could login as a guest - at least once. I tried switching to gdm instead lightdm, which seemed to do the trick, except the fact that it doesn't used the desired keyboard layout. But I couldn't use the GUI for changing to nouveau, also offered me only proprietary drivers. 
I tried to get lightdm working... somebody proposed regarding that problem to add a certain entry to the systemsource, which after sudo apt-get upgrade updated the unity-greeter, but didn't work for me. Adding the line "driver "noveau"" to my xorg.conf doesnt seem to make any difference. 

So current status: Not able to login using lightdm.


Edit1: xorg.conf, which, if I understood correctly, isn't really relevant for 12.04 anymore?
```

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection

```Xorg.0.log

```
[    33.518] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    33.518] X Protocol Version 11, Revision 0
[    33.518] Build Operating System: Linux 2.6.42-23-generic x86_64 Ubuntu
[    33.518] Current Operating System: Linux MK0 3.2.0-35-generic #55-Ubuntu SMP Wed Dec 5 17:42:16 UTC 2012 x86_64
[    33.518] Kernel command line: BOOT_IMAGE=/vmlinuz-3.2.0-35-generic root=/dev/mapper/MK0-root ro quiet splash
[    33.518] Build Date: 29 August 2012  12:12:33AM
[    33.518] xorg-server 2:1.11.4-0ubuntu10.8 (For technical support please see http://www.ubuntu.com/support) 
[    33.518] Current version of pixman: 0.24.4
[    33.518]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    33.518] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    33.518] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan  5 20:30:00 2013
[    33.519] (==) Using config file: "/etc/X11/xorg.conf"
[    33.519] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    33.521] (==) No Layout section.  Using the first Screen section.
[    33.521] (==) No screen section available. Using defaults.
[    33.521] (**) |-->Screen "Default Screen Section" (0)
[    33.521] (**) |   |-->Monitor "<default monitor>"
[    33.523] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[    33.523] (**) |   |-->Device "Default Device"
[    33.523] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    33.523] (==) Automatically adding devices
[    33.523] (==) Automatically enabling devices
[    33.524] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    33.524]     Entry deleted from font path.
[    33.524] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    33.524]     Entry deleted from font path.
[    33.524] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    33.524]     Entry deleted from font path.
[    33.524] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    33.524]     Entry deleted from font path.
[    33.524] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    33.524]     Entry deleted from font path.
[    33.524] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    33.524]     Entry deleted from font path.
[    33.524] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    33.524] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    33.524] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    33.524] (II) Loader magic: 0x7f182bbc7b00
[    33.524] (II) Module ABI versions:
[    33.524]     X.Org ANSI C Emulation: 0.4
[    33.524]     X.Org Video Driver: 11.0
[    33.524]     X.Org XInput driver : 16.0
[    33.524]     X.Org Server Extension : 6.0
[    33.525] (--) PCI:*(0:1:0:0) 10de:0191:1043:8233 rev 162, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf4000000/33554432, I/O @ 0x0000b000/128, BIOS @ 0x????????/131072
[    33.525] (II) Open ACPI successful (/var/run/acpid.socket)
[    33.525] (II) LoadModule: "extmod"
[    33.531] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    33.533] (II) Module extmod: vendor="X.Org Foundation"
[    33.533]     compiled for 1.11.3, module version = 1.0.0
[    33.533]     Module class: X.Org Server Extension
[    33.533]     ABI class: X.Org Server Extension, version 6.0
[    33.533] (II) Loading extension MIT-SCREEN-SAVER
[    33.533] (II) Loading extension XFree86-VidModeExtension
[    33.533] (II) Loading extension XFree86-DGA
[    33.533] (II) Loading extension DPMS
[    33.533] (II) Loading extension XVideo
[    33.533] (II) Loading extension XVideo-MotionCompensation
[    33.533] (II) Loading extension X-Resource
[    33.533] (II) LoadModule: "dbe"
[    33.533] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    33.534] (II) Module dbe: vendor="X.Org Foundation"
[    33.534]     compiled for 1.11.3, module version = 1.0.0
[    33.534]     Module class: X.Org Server Extension
[    33.534]     ABI class: X.Org Server Extension, version 6.0
[    33.534] (II) Loading extension DOUBLE-BUFFER
[    33.534] (II) LoadModule: "glx"
[    33.534] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    33.771] (II) Module glx: vendor="NVIDIA Corporation"
[    33.771]     compiled for 4.0.2, module version = 1.0.0
[    33.771]     Module class: X.Org Server Extension
[    33.771] (II) NVIDIA GLX Module  295.40  Thu Apr  5 21:57:38 PDT 2012
[    33.771] (II) Loading extension GLX
[    33.771] (II) LoadModule: "record"
[    33.771] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    33.773] (II) Module record: vendor="X.Org Foundation"
[    33.773]     compiled for 1.11.3, module version = 1.13.0
[    33.773]     Module class: X.Org Server Extension
[    33.773]     ABI class: X.Org Server Extension, version 6.0
[    33.773] (II) Loading extension RECORD
[    33.773] (II) LoadModule: "dri"
[    33.773] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    33.774] (II) Module dri: vendor="X.Org Foundation"
[    33.774]     compiled for 1.11.3, module version = 1.0.0
[    33.774]     ABI class: X.Org Server Extension, version 6.0
[    33.774] (II) Loading extension XFree86-DRI
[    33.774] (II) LoadModule: "dri2"
[    33.774] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    33.775] (II) Module dri2: vendor="X.Org Foundation"
[    33.775]     compiled for 1.11.3, module version = 1.2.0
[    33.775]     ABI class: X.Org Server Extension, version 6.0
[    33.775] (II) Loading extension DRI2
[    33.775] (==) Matched nvidia as autoconfigured driver 0
[    33.775] (==) Matched nouveau as autoconfigured driver 1
[    33.775] (==) Matched nv as autoconfigured driver 2
[    33.775] (==) Matched vesa as autoconfigured driver 3
[    33.775] (==) Matched fbdev as autoconfigured driver 4
[    33.775] (==) Assigned the driver to the xf86ConfigLayout
[    33.775] (II) LoadModule: "nvidia"
[    33.775] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    33.800] (II) Module nvidia: vendor="NVIDIA Corporation"
[    33.800]     compiled for 4.0.2, module version = 1.0.0
[    33.800]     Module class: X.Org Video Driver
[    33.807] (II) LoadModule: "nouveau"
[    33.807] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    33.812] (II) Module nouveau: vendor="X.Org Foundation"
[    33.812]     compiled for 1.11.3, module version = 0.0.16
[    33.812]     Module class: X.Org Video Driver
[    33.812]     ABI class: X.Org Video Driver, version 11.0
[    33.812] (II) LoadModule: "nv"
[    33.812] (WW) Warning, couldn't open module nv
[    33.812] (II) UnloadModule: "nv"
[    33.812] (II) Unloading nv
[    33.812] (EE) Failed to load module "nv" (module does not exist, 0)
[    33.812] (II) LoadModule: "vesa"
[    33.812] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    33.813] (II) Module vesa: vendor="X.Org Foundation"
[    33.813]     compiled for 1.11.3, module version = 2.3.0
[    33.813]     Module class: X.Org Video Driver
[    33.813]     ABI class: X.Org Video Driver, version 11.0
[    33.813] (II) LoadModule: "fbdev"
[    33.814] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    33.815] (II) Module fbdev: vendor="X.Org Foundation"
[    33.815]     compiled for 1.11.3, module version = 0.4.2
[    33.815]     ABI class: X.Org Video Driver, version 11.0
[    33.815] (==) Matched nvidia as autoconfigured driver 0
[    33.815] (==) Matched nouveau as autoconfigured driver 1
[    33.815] (==) Matched nv as autoconfigured driver 2
[    33.815] (==) Matched vesa as autoconfigured driver 3
[    33.815] (==) Matched fbdev as autoconfigured driver 4
[    33.815] (==) Assigned the driver to the xf86ConfigLayout
[    33.815] (II) LoadModule: "nvidia"
[    33.815] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    33.815] (II) Module nvidia: vendor="NVIDIA Corporation"
[    33.815]     compiled for 4.0.2, module version = 1.0.0
[    33.815]     Module class: X.Org Video Driver
[    33.815] (II) UnloadModule: "nvidia"
[    33.815] (II) Unloading nvidia
[    33.815] (II) Failed to load module "nvidia" (already loaded, 32536)
[    33.815] (II) LoadModule: "nouveau"
[    33.815] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    33.815] (II) Module nouveau: vendor="X.Org Foundation"
[    33.815]     compiled for 1.11.3, module version = 0.0.16
[    33.815]     Module class: X.Org Video Driver
[    33.815]     ABI class: X.Org Video Driver, version 11.0
[    33.815] (II) UnloadModule: "nouveau"
[    33.815] (II) Unloading nouveau
[    33.815] (II) Failed to load module "nouveau" (already loaded, 32536)
[    33.815] (II) LoadModule: "nv"
[    33.815] (WW) Warning, couldn't open module nv
[    33.815] (II) UnloadModule: "nv"
[    33.815] (II) Unloading nv
[    33.815] (EE) Failed to load module "nv" (module does not exist, 0)
[    33.815] (II) LoadModule: "vesa"
[    33.816] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    33.816] (II) Module vesa: vendor="X.Org Foundation"
[    33.816]     compiled for 1.11.3, module version = 2.3.0
[    33.816]     Module class: X.Org Video Driver
[    33.816]     ABI class: X.Org Video Driver, version 11.0
[    33.816] (II) UnloadModule: "vesa"
[    33.816] (II) Unloading vesa
[    33.816] (II) Failed to load module "vesa" (already loaded, 0)
[    33.816] (II) LoadModule: "fbdev"
[    33.816] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    33.816] (II) Module fbdev: vendor="X.Org Foundation"
[    33.816]     compiled for 1.11.3, module version = 0.4.2
[    33.816]     ABI class: X.Org Video Driver, version 11.0
[    33.816] (II) UnloadModule: "fbdev"
[    33.816] (II) Unloading fbdev
[    33.816] (II) Failed to load module "fbdev" (already loaded, 0)
[    33.816] (II) NVIDIA dlloader X Driver  295.40  Thu Apr  5 21:38:35 PDT 2012
[    33.816] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    33.818] (II) NOUVEAU driver Date:   Wed Nov 30 18:56:54 2011 +0100
[    33.818] (II) NOUVEAU driver for NVIDIA chipset families :
[    33.818]     RIVA TNT        (NV04)
[    33.818]     RIVA TNT2       (NV05)
[    33.818]     GeForce 256     (NV10)
[    33.818]     GeForce 2       (NV11, NV15)
[    33.818]     GeForce 4MX     (NV17, NV18)
[    33.818]     GeForce 3       (NV20)
[    33.818]     GeForce 4Ti     (NV25, NV28)
[    33.818]     GeForce FX      (NV3x)
[    33.818]     GeForce 6       (NV4x)
[    33.818]     GeForce 7       (G7x)
[    33.818]     GeForce 8       (G8x)
[    33.818]     GeForce GTX 200 (NVA0)
[    33.818]     GeForce GTX 400 (NVC0)
[    33.818] (II) VESA: driver for VESA chipsets: vesa
[    33.818] (II) FBDEV: driver for framebuffer: fbdev
[    33.818] (++) using VT number 7

[    33.821] (II) Loading sub module "fb"
[    33.821] (II) LoadModule: "fb"
[    33.822] (II) Loading /usr/lib/xorg/modules/libfb.so
[    33.825] (II) Module fb: vendor="X.Org Foundation"
[    33.825]     compiled for 1.11.3, module version = 1.0.0
[    33.825]     ABI class: X.Org ANSI C Emulation, version 0.4
[    33.825] (II) Loading sub module "wfb"
[    33.825] (II) LoadModule: "wfb"
[    33.825] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    33.828] (II) Module wfb: vendor="X.Org Foundation"
[    33.828]     compiled for 1.11.3, module version = 1.0.0
[    33.828]     ABI class: X.Org ANSI C Emulation, version 0.4
[    33.828] (II) Loading sub module "ramdac"
[    33.828] (II) LoadModule: "ramdac"
[    33.828] (II) Module "ramdac" already built-in
[    33.832] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    33.832] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    33.832] (II) Loading /usr/lib/xorg/modules/libfb.so
[    33.836] (WW) Falling back to old probe method for vesa
[    33.836] (WW) Falling back to old probe method for fbdev
[    33.836] (II) Loading sub module "fbdevhw"
[    33.836] (II) LoadModule: "fbdevhw"
[    33.837] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    33.837] (II) Module fbdevhw: vendor="X.Org Foundation"
[    33.837]     compiled for 1.11.3, module version = 0.0.2
[    33.837]     ABI class: X.Org Video Driver, version 11.0
[    33.837] (EE) open /dev/fb0: No such file or directory
[    33.837] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    33.837] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    33.837] (==) NVIDIA(0): RGB weight 888
[    33.837] (==) NVIDIA(0): Default visual is TrueColor
[    33.837] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    33.837] (**) NVIDIA(0): Option "NoLogo" "True"
[    33.838] (**) NVIDIA(0): Enabling 2D acceleration
[    33.843] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
[    33.843] (EE) NVIDIA(0):     system's kernel log for additional error messages and
[    33.843] (EE) NVIDIA(0):     consult the NVIDIA README for details.
[    33.843] (EE) NVIDIA(0):  *** Aborting ***
[    33.843] (II) UnloadModule: "nvidia"
[    33.843] (II) Unloading nvidia
[    33.843] (II) UnloadModule: "wfb"
[    33.843] (II) Unloading wfb
[    33.843] (II) UnloadModule: "fb"
[    33.843] (II) Unloading fb
[    33.843] (EE) Screen(s) found, but none have a usable configuration.
[    33.843] 
Fatal server error:
[    33.843] no screens found
[    33.843] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    33.844] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    33.844] 
[    33.846]  ddxSigGiveUp: Closing log
[    33.846] Server terminated with error (1). Closing log file.
 
```

---

