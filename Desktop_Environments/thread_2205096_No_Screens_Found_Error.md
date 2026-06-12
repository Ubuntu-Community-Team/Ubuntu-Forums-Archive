---
title: "No Screens Found Error"
date: 2014-02-12
forum: Desktop Environments
---

### Post by cardude1 on 2014-02-12
I have searched these forums and found all kinds of posts with this error, but none of them seem to fix the problem.  I have Ubuntu 13.10 with Ubuntu Desktop and when I try to run startx I get the error, "No Screens Found".

Any clue how this can be fixed?

```

[  3210.635] 
X.Org X Server 1.14.5
Release Date: 2013-12-12
[  3210.635] X Protocol Version 11, Revision 0
[  3210.635] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[  3210.635] Current Operating System: Linux localhost 3.12.9-x86_64-linode37 #1 SMP Mon Feb 3 10:01:02 EST 2014 x86_64
[  3210.635] Kernel command line: root=/dev/xvda xencons=tty console=tty1 console=hvc0 nosep nodevfs ramdisk_size=32768 ip_conntrack.hashsize=8192 nf_conntrack.hashsize=8192 ro  devtmpfs.mount=1 
[  3210.635] Build Date: 17 December 2013  10:06:15AM
[  3210.635] xorg-server 2:1.14.5-1ubuntu2~saucy1 (For technical support please see http://www.ubuntu.com/support) 
[  3210.635] Current version of pixman: 0.30.2
[  3210.635] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[  3210.635] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  3210.635] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Feb 12 06:03:47 2014
[  3210.636] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  3210.636] (==) No Layout section.  Using the first Screen section.
[  3210.636] (==) No screen section available. Using defaults.
[  3210.636] (**) |-->Screen "Default Screen Section" (0)
[  3210.636] (**) |   |-->Monitor "<default monitor>"
[  3210.636] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[  3210.636] (==) Automatically adding devices
[  3210.636] (==) Automatically enabling devices
[  3210.636] (==) Automatically adding GPU devices
[  3210.636] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  3210.636] 	Entry deleted from font path.
[  3210.636] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  3210.636] 	Entry deleted from font path.
[  3210.636] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  3210.636] 	Entry deleted from font path.
[  3210.636] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  3210.636] 	Entry deleted from font path.
[  3210.636] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  3210.636] 	Entry deleted from font path.
[  3210.636] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[  3210.636] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  3210.636] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[  3210.636] (II) Loader magic: 0x7f8b6097fd20
[  3210.636] (II) Module ABI versions:
[  3210.636] 	X.Org ANSI C Emulation: 0.4
[  3210.636] 	X.Org Video Driver: 14.1
[  3210.636] 	X.Org XInput driver : 19.1
[  3210.636] 	X.Org Server Extension : 7.0
[  3210.637] (II) Open ACPI successful (/var/run/acpid.socket)
[  3210.637] Initializing built-in extension Generic Event Extension
[  3210.637] Initializing built-in extension SHAPE
[  3210.637] Initializing built-in extension MIT-SHM
[  3210.637] Initializing built-in extension XInputExtension
[  3210.637] Initializing built-in extension XTEST
[  3210.637] Initializing built-in extension BIG-REQUESTS
[  3210.637] Initializing built-in extension SYNC
[  3210.637] Initializing built-in extension XKEYBOARD
[  3210.637] Initializing built-in extension XC-MISC
[  3210.637] Initializing built-in extension SECURITY
[  3210.637] Initializing built-in extension XINERAMA
[  3210.637] Initializing built-in extension XFIXES
[  3210.637] Initializing built-in extension RENDER
[  3210.637] Initializing built-in extension RANDR
[  3210.637] Initializing built-in extension COMPOSITE
[  3210.637] Initializing built-in extension DAMAGE
[  3210.637] Initializing built-in extension MIT-SCREEN-SAVER
[  3210.637] Initializing built-in extension DOUBLE-BUFFER
[  3210.637] Initializing built-in extension RECORD
[  3210.637] Initializing built-in extension DPMS
[  3210.637] Initializing built-in extension X-Resource
[  3210.637] Initializing built-in extension XVideo
[  3210.637] Initializing built-in extension XVideo-MotionCompensation
[  3210.637] Initializing built-in extension SELinux
[  3210.637] Initializing built-in extension XFree86-VidModeExtension
[  3210.637] Initializing built-in extension XFree86-DGA
[  3210.637] Initializing built-in extension XFree86-DRI
[  3210.637] Initializing built-in extension DRI2
[  3210.637] (II) "glx" will be loaded by default.
[  3210.637] (WW) "xmir" is not to be loaded by default. Skipping.
[  3210.637] (II) LoadModule: "dri2"
[  3210.637] (II) Module "dri2" already built-in
[  3210.637] (II) LoadModule: "glamoregl"
[  3210.637] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[  3210.639] (II) Module glamoregl: vendor="X.Org Foundation"
[  3210.639] 	compiled for 1.14.3, module version = 0.5.1
[  3210.639] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  3210.639] (II) LoadModule: "glx"
[  3210.639] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  3210.640] (II) Module glx: vendor="X.Org Foundation"
[  3210.640] 	compiled for 1.14.5, module version = 1.0.0
[  3210.640] 	ABI class: X.Org Server Extension, version 7.0
[  3210.640] (==) AIGLX enabled
[  3210.640] Loading extension GLX
[  3210.640] (==) Matched vesa as autoconfigured driver 0
[  3210.640] (==) Matched modesetting as autoconfigured driver 1
[  3210.640] (==) Matched fbdev as autoconfigured driver 2
[  3210.640] (==) Assigned the driver to the xf86ConfigLayout
[  3210.640] (II) LoadModule: "vesa"
[  3210.640] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  3210.640] (II) Module vesa: vendor="X.Org Foundation"
[  3210.640] 	compiled for 1.14.1, module version = 2.3.2
[  3210.640] 	Module class: X.Org Video Driver
[  3210.640] 	ABI class: X.Org Video Driver, version 14.1
[  3210.640] (II) LoadModule: "modesetting"
[  3210.640] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  3210.640] (II) Module modesetting: vendor="X.Org Foundation"
[  3210.640] 	compiled for 1.14.1, module version = 0.8.0
[  3210.640] 	Module class: X.Org Video Driver
[  3210.640] 	ABI class: X.Org Video Driver, version 14.1
[  3210.640] (II) LoadModule: "fbdev"
[  3210.641] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  3210.641] (II) Module fbdev: vendor="X.Org Foundation"
[  3210.641] 	compiled for 1.14.1, module version = 0.4.3
[  3210.641] 	Module class: X.Org Video Driver
[  3210.641] 	ABI class: X.Org Video Driver, version 14.1
[  3210.641] (II) VESA: driver for VESA chipsets: vesa
[  3210.641] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[  3210.641] (II) FBDEV: driver for framebuffer: fbdev
[  3210.641] (--) using VT number 2

[  3210.641] (WW) Falling back to old probe method for vesa
[  3210.641] (WW) Falling back to old probe method for modesetting
[  3210.641] (EE) open /dev/dri/card0: No such file or directory
[  3210.641] (WW) Falling back to old probe method for fbdev
[  3210.641] (II) Loading sub module "fbdevhw"
[  3210.641] (II) LoadModule: "fbdevhw"
[  3210.641] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  3210.641] (II) Module fbdevhw: vendor="X.Org Foundation"
[  3210.642] 	compiled for 1.14.5, module version = 0.0.2
[  3210.642] 	ABI class: X.Org Video Driver, version 14.1
[  3210.642] (EE) open /dev/fb0: No such file or directory
[  3210.642] (EE) No devices detected.
[  3210.642] (==) Matched vesa as autoconfigured driver 0
[  3210.642] (==) Matched modesetting as autoconfigured driver 1
[  3210.642] (==) Matched fbdev as autoconfigured driver 2
[  3210.642] (==) Assigned the driver to the xf86ConfigLayout
[  3210.642] (II) LoadModule: "vesa"
[  3210.642] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  3210.642] (II) Module vesa: vendor="X.Org Foundation"
[  3210.642] 	compiled for 1.14.1, module version = 2.3.2
[  3210.642] 	Module class: X.Org Video Driver
[  3210.642] 	ABI class: X.Org Video Driver, version 14.1
[  3210.642] (II) UnloadModule: "vesa"
[  3210.642] (II) Unloading vesa
[  3210.642] (II) Failed to load module "vesa" (already loaded, 32651)
[  3210.642] (II) LoadModule: "modesetting"
[  3210.642] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  3210.642] (II) Module modesetting: vendor="X.Org Foundation"
[  3210.642] 	compiled for 1.14.1, module version = 0.8.0
[  3210.642] 	Module class: X.Org Video Driver
[  3210.642] 	ABI class: X.Org Video Driver, version 14.1
[  3210.642] (II) UnloadModule: "modesetting"
[  3210.642] (II) Unloading modesetting
[  3210.642] (II) Failed to load module "modesetting" (already loaded, 32651)
[  3210.642] (II) LoadModule: "fbdev"
[  3210.642] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  3210.642] (II) Module fbdev: vendor="X.Org Foundation"
[  3210.642] 	compiled for 1.14.1, module version = 0.4.3
[  3210.642] 	Module class: X.Org Video Driver
[  3210.642] 	ABI class: X.Org Video Driver, version 14.1
[  3210.642] (II) UnloadModule: "fbdev"
[  3210.642] (II) Unloading fbdev
[  3210.642] (II) Failed to load module "fbdev" (already loaded, 32651)
[  3210.642] (II) VESA: driver for VESA chipsets: vesa
[  3210.642] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[  3210.642] (II) FBDEV: driver for framebuffer: fbdev
[  3210.643] (++) using VT number 2

[  3210.643] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[  3210.643] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[  3210.643] (WW) Falling back to old probe method for vesa
[  3210.643] (WW) Falling back to old probe method for modesetting
[  3210.643] (EE) open /dev/dri/card0: No such file or directory
[  3210.643] (EE) open /dev/dri/card0: No such file or directory
[  3210.643] (WW) Falling back to old probe method for fbdev
[  3210.643] (II) Loading sub module "fbdevhw"
[  3210.643] (II) LoadModule: "fbdevhw"
[  3210.643] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  3210.643] (II) Module fbdevhw: vendor="X.Org Foundation"
[  3210.643] 	compiled for 1.14.5, module version = 0.0.2
[  3210.643] 	ABI class: X.Org Video Driver, version 14.1
[  3210.643] (EE) open /dev/fb0: No such file or directory
[  3210.643] (EE) No devices detected.
[  3210.643] (EE) 
Fatal server error:
[  3210.643] (EE) no screens found(EE) 
[  3210.643] (EE) 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[  3210.643] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  3210.643] (EE) 
[  3210.643] (EE) Server terminated with error (1). Closing log file.


```

---

### Post by Bucky Ball on 2014-02-12
sudo service lightdm start

... is what you should be using. Startx does nothing for Unity. That command is for Gnome. Also, if you are running this:

Linux 3.2.0-37-generic

You haven't updated/upgraded in awhile. 12.04 is currently running the 3.2.0-58 kernel.

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

... will upgrade all things that need it in your current release, NOT upgrade you to a newer release. ;)

---

### Post by cardude1 on 2014-02-12
Unfortunately when I try sudo service lightdm start I get the error start: Job failed to start.

I also ran the lines to upgrade my current release and that seemed to work fine.

Thanks!

EDIT:
I also tried to re-install lightdm and get the same error
sudo apt-get update
sudo apt-get install aptitude
sudo aptitude reinstall lightdm
sudo service lightdm start
start: Job failed to start

Here is the log - 
```

[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.8.4, UID=0 PID=5522
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/10-ubuntu.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-unity-greeter.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Registered seat module unity
[+0.00s] DEBUG: Registered seat module surfaceflinger
[+0.00s] DEBUG: Adding default seat
[+0.00s] DEBUG: Seat: Starting
[+0.00s] DEBUG: Seat: Creating greeter session
[+0.00s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+0.00s] DEBUG: Seat: Creating display server of type x
[+0.00s] DEBUG: Seat: Starting local X display
[+0.00s] DEBUG: Using VT 7
[+0.00s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+0.00s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+0.00s] DEBUG: DisplayServer x-0: Launching X Server
[+0.00s] DEBUG: Launching process 5529: /usr/bin/X -core :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.00s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+0.00s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.13s] DEBUG: Process 5529 terminated with signal 6
[+0.13s] DEBUG: DisplayServer x-0: X server stopped
[+0.13s] DEBUG: Releasing VT 7
[+0.13s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+0.13s] DEBUG: Seat: Display server stopped
[+0.13s] DEBUG: Seat: Stopping; greeter display server failed to start
[+0.13s] DEBUG: Seat: Stopping
[+0.13s] DEBUG: Seat: Stopping session
[+0.13s] DEBUG: Seat: Session stopped
[+0.13s] DEBUG: Seat: Stopped
[+0.13s] DEBUG: Required seat has stopped
[+0.13s] DEBUG: Stopping display manager
[+0.13s] DEBUG: Display manager stopped
[+0.13s] DEBUG: Stopping daemon
[+0.13s] DEBUG: Seat: Stopping session
[+0.13s] DEBUG: Releasing VT 7
[+0.13s] DEBUG: Exiting with return value 1


```

---

### Post by Yellow Pasque on 2014-02-13
@OP: Why are you running a custom kernel? What GPU do you have and what driver are you trying to use?

> **Bucky Ball said:**
> if you are running this: Linux 3.2.0-37-generic
You haven't updated/upgraded in awhile. 12.04 is currently running the 3.2.0-58 kernel.

The user is running Ubuntu 13.10 and using a custom (3.12.x) kernel.  3.2.0-37-generic was the kernel Ubuntu's build server was running when X was compiled..

---

### Post by cardude1 on 2014-02-13
I was trying to get this work on Linode and that is what they installed.

Any clue how to fix this?

---

### Post by Yellow Pasque on 2014-02-13
What GPU do you have and what driver are you trying to use?

---

