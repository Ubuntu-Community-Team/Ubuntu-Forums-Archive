---
title: "Problem German Keyboard Alt GR and special Keys + copy from terminal - nubuntu"
date: 2006-09-25
forum: Desktop Environments
---

### Post by dschmid on 2006-09-25
Hello, I setup nubuntu (a dapper based ubuntu distri with fluxbox instead of gnome or kde) yesterday on my Acer Aspire Notebook and now i have two problems left. Usualy i'm using only the touchpad.

1: My Notebook got a German Keyboard. Before doing startx as user admin (created on installation process) all keys work fine. But in fluxbox all special Keys with "alt gr" and german special keys don't work. In vmware images the keys work. Also when I do ```

sudo startx
``` all is ok. I had tried to add the new user dirk but thats won't work too. So it had to be something with the userrights I think. My /etc/X11/xorg.conf:
```

Section "Files"
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
# path to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "de"
Option "XkbVariant" "nodeadkeys"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
Identifier "ATI Technologies, Inc. M9+ 5C61 [Radeon Mobility 9000 (AGP)]"
Driver "ati"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-64
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. M9+ 5C61 [Radeon Mobility 9000 (AGP)]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x800"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
Mode 0666
EndSection
```


And thats the important part of /var/log/Xorg.0.log i think:

```
(II) Module theatre_detect: vendor="X.Org Foundation"
compiled for 7.0.0, module version = 1.0.0
ABI class: X.Org Video Driver, version 0.8
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(**) RADEON(0): RADEONScreenInit finished
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "de"
(**) Generic Keyboard: XkbLayout: "de"
(**) Option "XkbVariant" "nodeadkeys"
(**) Generic Keyboard: XkbVariant: "nodeadkeys"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(WW) Couldn't load XKB keymap, falling back to pre-XKB keymap sad.gif :( // I think here is the problem
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
No such file or directory.
Error opening /dev/wacom : Invalid argument
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(**) RADEON(0): RADEONSaveScreen(2)
(**) RADEON(0): RADEONSaveScreen(0)
(**) RADEON(0): RADEONSaveScreen(1)

```

And here my /etc/group:
```
 root:x:0:admin
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:admin
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:admin
fax:x:21:
voice:x:22:
cdrom:x:24:hal,haldaemon,admin
floppy:x:25:hal,haldaemon,admin
tape:x:26:
sudo:x:27:
audio:x:29:admin
dip:x:30:admin
www-data:x:34:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:admin
sasl:x:45:
plugdev:x:46:hal,haldaemon,admin
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
klog:x:102:
syslog:x:103:
crontab:x:104:
ssh:x:105:
lpadmin:x:106:admin
messagebus:x:107:
hal:x:108:
slocate:x:109:
scanner:x:110:admin
haldaemon:x:111:
admin:x:1000:admin,dirk
 
``` 

And here is the /etc/passwd:

```
 root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
dhcp:x:101:101::/nonexistent:/bin/false
klog:x:102:102::/home/klog:/bin/false
syslog:x:103:103::/home/syslog:/bin/false
messagebus:x:104:107::/var/run/dbus:/bin/false
hal:x:108:108:Hardware abstraction layer,,,:/var/run/hal:/bin/false
nstxd:x:100:65534::/var/run/nstxd:/bin/false
haldaemon:x:111:111:Hardware abstraction layer,,,:/var/run/hal:/bin/false
admin:x:1000:1000:admin,,,:/home/admin:/bin/bash
gkrellmd:x:105:65534::/var/run:/bin/false
sshd:x:106:65534::/var/run/sshd:/bin/false
dirk:x:1001:1000::/home/dirk:/bin/sh
 
```


I have seen that somebody post the same problem in june but without an answer. I hope someone had the same problem since then and hopefully fixed it. Over google I found many posts discussing this problem but I didn't found a working solve.

2: Because I'm using a touchpad (synaptics) I don't have a middle mouse button and can't do copy from the terminal. Paste work with shift+insert. Is there a way to copy with a shortcut like this???

---

