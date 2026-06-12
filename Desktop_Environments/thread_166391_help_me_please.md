---
title: "help me please"
date: 2006-04-26
forum: Desktop Environments
---

### Post by lildevil on 2006-04-26
hi , 
im a new user as i have just found this version 
i have loaded it and all without a problem 
my issue is that now im into it everytime i try to open a folder (most times ) or go to a download page and download anything 
and even just into here i keep getting an issue that my system just closes and comes back my logon screen, i can log back in and anoly lose what i was just doing 
i have replaced ram ,video card,usb  connectors,all other removable parts to no avail 
i have an amd 3000+ cpu with a gigbyte k7 triton 400 board and 1gb ddr ram 
1 x 40gb hard drive , 1 x 80gb hard drive . 1 x dvd burner dual layer and a dvd rom ,i also have an 80 gb hard drive running of the onboard raid 
i have a friend that is quite conversant with linux and it even has him stumped please can you adives of any ideas asap as im now lost i have also done all the updates ect needed for all hardware and software 
i await help in anticipation 
regards
alan

---

### Post by Ramses de Norre on 2006-04-26
```
less /var/log/Xorg.0.log.old
less ~/.xsession-errors
```
Are there any error messages in one of these files?

---

### Post by lildevil on 2006-04-26
im sorry im very new how do i find what your asking ?

---

### Post by Ramses de Norre on 2006-04-26
Type those commands in terminal one by one (applications>system tools>terminal) or if the graphics crash before you're able to do so press alt+ctrl+F1 and enter them there, press q after you've read and copied the contents to get back to the prompt. If you don't know how to find the errors you can post both files here and we'll have a look at it.

---

### Post by lildevil on 2006-04-26
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "alan"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/lildevilcomp:/tmp/.ICE-unix/5906
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(epiphany-browser:6037): libgnomevfs-WARNING **: Failed to create service browser: Bad state
 is this what u asked for?

---

### Post by Ramses de Norre on 2006-04-26
Is there more inside the files? I don't see anything obvious pointing to the reason why X is crashing.

---

### Post by lildevil on 2006-04-26
first line i ytpe gives me the following 
alan@lildevilcomp:~$ less /var/log/xorg.0.log.old
/var/log/xorg.0.log.old: No such file or directory
alan@lildevilcomp:~$

second line i type gives me following 

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "alan"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/lildevilcomp:/tmp/.ICE-unix/5906
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(epiphany-browser:6037): libgnomevfs-WARNING **: Failed to create service browser: Bad state

/home/alan/.xsession-errors (END)
thats all i can see 

i hope this helps

---

### Post by Ramses de Norre on 2006-04-26
```
less /var/log/**X**org.0.log.old
``` commands are case sensitive.

---

### Post by lildevil on 2006-04-26
sorry is this better ? 

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux lildevilcomp 2.6.15-21-386 #1 PREEMPT Fri Apr 21 16:43:33 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Apr 26 22:40:06 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
/var/log/Xorg.0.log.old

---

### Post by Ramses de Norre on 2006-04-26
There should be more, look for lines starting with (EE) at the end of the file. (press down arrow to navigate through file, and ignore font rendering errors)

---

### Post by lildevil on 2006-04-26
sorry keeps doing it 
this is last part cant see anything starts with ee 

(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4, 5, 6 and 7
(**) Configured Mouse: Buttons: 11
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x86) [0x80b4a56]
1: [0xffffe420]

Fatal server error:
Caught signal 11.  Server aborting

(END)

---

### Post by lildevil on 2006-04-26
next part up 
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
error opening security policy file /etc/X11/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
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
(**) Configured Mouse: ZAxisMapping: buttons 4, 5, 6 and 7
(**) Configured Mouse: Buttons: 11
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.
:

---

### Post by lildevil on 2006-04-26
sorry but this is only way i can do it  hope this is enough to help above that 
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Indirect CPU to Screen color expansion
        Solid Lines
        Scanline Image Writes
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                32 128x128 slots
                32 256x256 slots
                16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(**) Option "dpms"
(**) NV(0): DPMS enabled
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
error opening security policy file /etc/X11/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"

---

### Post by lildevil on 2006-04-26
sorry just had more updates and got this error does it help? 

E: /var/cache/apt/archives/xserver-xorg_7.0.0-0ubuntu31_i386.deb: subprocess pre-installation script returned error exit status 2

---

### Post by lildevil on 2006-04-27
i seem to have fixed the problem 
it all seems to have evolved from nvidia drivers once we installed newer drivers it has stopped doing the relogin thing 
thanks to all that tried to help :)

---

