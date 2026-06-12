---
title: "After intalling Virtualbox and python2.3, only command line mode"
date: 2009-04-21
forum: General Help
---

### Post by kwakhyok on 2009-04-21
Hi, there. I would like to ask some experts here about my ubuntu recovery. I've installed the Virtualbox along with python2.3. During installing python2.3 in apt, a warning pop up and ask me make sure if I would really want to uninstall some essential items. Unfortunately, I ignored these messages without patience and care. When I restarted, I only got a command line mode of ubuntu. No matter what I select, either recovery mode or normal start, neither can bring me to the nvidia screen following a desktop environment.

My computer is Lenovo T61p with nvidia Quadro FX570M, the version of Ubuntu is 8.04.

Could you guys give me some hints about how can I return to my last correct settings? I am still able to run some command on verbose mode.

Many thanks in advance.

---

### Post by prshah on 2009-04-21
> **kwakhyok said:**
>  I only got a command line mode of ubuntu. 

From the command line, give the command ```
startx
``` If it does not load the GUI, please post back the output (about last 10 lines) from the command for clues to the problem.

---

### Post by kwakhyok on 2009-04-21
Thanks a lot. prshah

I followed your suggestion and got the splash of Nvidia, then it seemed to fail in loading GNome.
the messages is as follows:

Failed to load module "type1"
_____________________________________________________
expected keysym, got XF86kbdLightOnoff xxx
expected keysym, got XF86kbdBrightnessdown xxxx
expected keysym, got XF86kbdLightOnoff xxx
waiting for for x server to shut down
Freefontpath: refcount is 2, should be 1, fixing...
_____________________________________________________

I've checked the /var/log/Xorg.o.log as well. I am posting 10 last lines
_______________________________________________________
(**) Mouse0: ZAxisMapping: buttons 4 and 5
(**) Mouse0: Buttons: 9
(**) Mouse0: Sensitivity: 1
(II) evaluating device (Mouse0)
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(II) evaluating device (Keyboard0)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(--) Mouse0: PnP-detected protocol: "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.


_______________________________________________________


Thanks in advance

---

### Post by kwakhyok on 2009-04-21
I extracted some message from syslog, maybe it has something to do with my issue.
syslog:
_________________________________________________

Apr 20 22:59:05 yi-laptop kernel: [   24.701797] nvidia: module license 'NVIDIA' taints kernel.
Apr 20 22:59:05 yi-laptop kernel: [   24.952519] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 20 22:59:05 yi-laptop kernel: [   24.952529] PCI: Setting latency timer of device 0000:01:00.0 to 64
Apr 20 22:59:05 yi-laptop kernel: [   24.952648] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.12  Thu Jul 17 18:11:36 PDT 2008
.....
.....

Apr 21 11:43:50 yi-laptop kernel: [   45.195396] scim-launcher[6937]: segfault at b79ece6c eip b79ece6c esp bf805bcc error 4
Apr 21 11:43:50 yi-laptop console-kit-daemon[6179]: WARNING: Unable to activate console: No such device or address 
Apr 21 11:45:01 yi-laptop /USR/SBIN/CRON[6999]: (root) CMD (   if [ -d /var/lock/mrtg ]; then if [ -x /usr/bin/mrtg ] && [ -r /etc/mrtg.cfg ]; then env LANG=C /usr/bin/mrtg /etc/mrtg.cfg >> /var/log/mrtg/mrtg.log 2>&1; fi else mkdir /var/lock/mrtg; fi)
Apr 21 11:47:36 yi-laptop init: tty4 main process (5115) killed by TERM signal
Apr 21 11:47:36 yi-laptop init: tty5 main process (5116) killed by TERM signal
Apr 21 11:47:36 yi-laptop init: tty1 main process (6803) killed by TERM signal
Apr 21 11:47:36 yi-laptop init: tty2 main process (5118) killed by TERM signal
Apr 21 11:47:36 yi-laptop init: tty3 main process (5120) killed by TERM signal
Apr 21 11:47:36 yi-laptop init: tty6 main process (5122) killed by TERM signal
Apr 21 11:47:36 yi-laptop avahi-daemon[5593]: Got SIGTERM, quitting.
Apr 21 11:47:36 yi-laptop avahi-daemon[5593]: Leaving mDNS multicast group on interface eth0.IPv4 with address 130.60.155.224.
Apr 21 11:47:39 yi-laptop cvsd[5641]: caught signal SIGTERM (15), shutting down
Apr 21 11:47:39 yi-laptop cvsd[5641]: version 1.0.14 bailing out
________________________________________________

---

### Post by kwakhyok on 2009-04-21
> **prshah said:**
> From the command line, give the command ```
startx
``` If it does not load the GUI, please post back the output (about last 10 lines) from the command for clues to the problem.

some message extracted from dpkg.log

2009-04-20 18:16:01 status installed python2.3 2.3.5-9ubuntu1.2
2009-04-20 18:16:02 status triggers-pending libc6 2.7-10ubuntu4
2009-04-20 18:16:02 trigproc libc6 2.7-10ubuntu4 2.7-10ubuntu4
2009-04-20 18:16:02 status half-configured libc6 2.7-10ubuntu4
2009-04-20 18:16:02 status installed libc6 2.7-10ubuntu4
2009-04-20 18:18:09 startup archives unpack
2009-04-20 18:18:09 install libssl0.9.7 <none> 0.9.7g-5ubuntu1.1
2009-04-20 18:18:09 status half-installed libssl0.9.7 0.9.7g-5ubuntu1.1
2009-04-20 18:18:10 status unpacked libssl0.9.7 0.9.7g-5ubuntu1.1
2009-04-20 18:18:10 status unpacked libssl0.9.7 0.9.7g-5ubuntu1.1
2009-04-20 18:18:10 install virtualbox-2.2 <none> 2.2.0-45846_xandros4.1
2009-04-20 18:18:10 status half-installed virtualbox-2.2 2.2.0-45846_xandros4.1
2009-04-20 18:18:25 status unpacked virtualbox-2.2 2.2.0-45846_xandros4.1
2009-04-20 18:18:25 status unpacked virtualbox-2.2 2.2.0-45846_xandros4.1
2009-04-20 18:18:26 startup packages configure
2009-04-20 18:18:26 configure libssl0.9.7 0.9.7g-5ubuntu1.1 0.9.7g-5ubuntu1.1
2009-04-20 18:18:26 status unpacked libssl0.9.7 0.9.7g-5ubuntu1.1
2009-04-20 18:18:26 status half-configured libssl0.9.7 0.9.7g-5ubuntu1.1
2009-04-20 18:18:27 status installed libssl0.9.7 0.9.7g-5ubuntu1.1
2009-04-20 18:18:27 status triggers-pending libc6 2.7-10ubuntu4
2009-04-20 18:18:27 configure virtualbox-2.2 2.2.0-45846_xandros4.1 2.2.0-45846_xandros4.1
2009-04-20 18:18:27 status unpacked virtualbox-2.2 2.2.0-45846_xandros4.1
2009-04-20 18:18:27 status unpacked virtualbox-2.2 2.2.0-45846_xandros4.1
2009-04-20 18:18:27 status half-configured virtualbox-2.2 2.2.0-45846_xandros4.1
2009-04-20 18:20:22 status installed virtualbox-2.2 2.2.0-45846_xandros4.1
2009-04-20 18:20:22 trigproc libc6 2.7-10ubuntu4 2.7-10ubuntu4
2009-04-20 18:20:22 status half-configured libc6 2.7-10ubuntu4
2009-04-20 18:20:23 status installed libc6 2.7-10ubuntu4

---

### Post by kwakhyok on 2009-04-21
> **prshah said:**
> From the command line, give the command ```
startx
``` If it does not load the GUI, please post back the output (about last 10 lines) from the command for clues to the problem.

some logs extracted from /var/log/gdm/_0.log

***************************************************************

Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 20 11:09:35 2009
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module "ddc" already built-in
(II) Module "ramdac" already built-in
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
Atom 4, CARD32 4, unsigned long 4
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled

---

### Post by kwakhyok on 2009-04-21
does it have anything to do with "Kernel complie", if so, I will recompilie the kernel.

---

### Post by prshah on 2009-04-21
> **kwakhyok said:**
> 
Failed to load module "type1"


AFAIK the type1 module is completely superseded by the "freetype" module; are you using an old xorg.conf? What is the output of the command```
cat /etc/X11/xorg.conf | grep -i type1
```

If the above command does show a "type1" module loading, edit the xorg.conf file and comment out that line by placing a "#" in front of it.

```
sudo nano /etc/X11/xorg.conf
```

Use Ctrl+O (writeOut) to save and Ctrl+X to exit. Then try the startx command again.

---

### Post by kwakhyok on 2009-04-21
> **prshah said:**
> AFAIK the type1 module is completely superseded by the "freetype" module; are you using an old xorg.conf? What is the output of the command```
cat /etc/X11/xorg.conf | grep -i type1
```

If the above command does show a "type1" module loading, edit the xorg.conf file and comment out that line by placing a "#" in front of it.

```
sudo nano /etc/X11/xorg.conf
```

Use Ctrl+O (writeOut) to save and Ctrl+X to exit. Then try the startx command again.


Thanks a lot. I followed your suggestion. The "type1" error message doesn't appear. However, it still doesn't work so far.

I didn't use the old xorg.conf.

The output is like that: a NVdia splash screen comes out shortly and then is followed by a screen full of dots, the mouse icon becomes black cross. Then the system fails to load GUI and goes to command line.

the last lines of Xorg.0.log file is as follows:
```

(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) NVIDIA(0):     enough to receive ACPI display change hotkey events.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Keyboard0: always reports core events
(**) Option "Protocol" "standard"
(**) Keyboard0: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard0: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard0: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard0: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(**) Option "Protocol" "auto"
(**) Mouse0: Device: "/dev/psaux"
(**) Mouse0: Protocol: "auto"
(**) Option "CorePointer"
(**) Mouse0: always reports core events
(**) Option "Device" "/dev/psaux"
(**) Option "Emulate3Buttons" "no"
(**) Option "ZAxisMapping" "4 5"
(**) Mouse0: ZAxisMapping: buttons 4 and 5
(**) Mouse0: Buttons: 9
(**) Mouse0: Sensitivity: 1
(II) evaluating device (Mouse0)
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(II) evaluating device (Keyboard0)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(--) Mouse0: PnP-detected protocol: "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.

```

---

