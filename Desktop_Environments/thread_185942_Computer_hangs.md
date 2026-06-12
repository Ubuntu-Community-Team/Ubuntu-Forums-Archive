---
title: "Computer hangs"
date: 2006-06-01
forum: Desktop Environments
---

### Post by prawdapunk on 2006-06-01
Hello !

I installed the newest version of Ubuntu, but I have a one, big problem - computer hangs still and only hard restart helps.

I really don't know why I have this problem, but it makes impossible to work on Ubuntu 6.06.

Problem steps out in the most unforeseeable moments - when I'm starting two applications, when I marking icons, but the most often steps out, when I'm surfing in Firefox - the two tags on me intrude, they shine or somthing else...

I really don;t know why I have this problem, because in the earlier version I didn't have any problems.

I have GF 6600 GT and this hardware can by perpetrator ?

---

### Post by Ramses de Norre on 2006-06-01
Any error messages in /var/log/Xorg.0.log.old or ~/.xsession-errors ?

---

### Post by prawdapunk on 2006-06-01
> (==) NV(0): Backing store disabled
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

> (II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded

I think that it can be o source of my problems, but I really don't know oneself on this.

---

### Post by Ramses de Norre on 2006-06-01
That wacom thing is nothing to worry about, something automaticaly set in your xorg.conf (I commented it out).
Is that all in those two files?

---

### Post by prawdapunk on 2006-06-01
From what I noticed, then all mistakes, but full version of this messages, you can find there: [http://ibw.com.pl/maciek/](http://ibw.com.pl/maciek/)

---

### Post by jvictor on 2006-07-03
I to had this same prob on a FX5200 while using nvidia drivers.. I blacklisted amd64_agp , agpgart
and had to enable SBA and Fastwrites to prevent crashing. Now it works fine.It was so annoying and made dapper worse hatn win 95 !!

If u are using a via mobo u may need to black list via-agp

another option u can try is using the line

Option "NvAgp"  "0"

in ur device section of /etc/X11/xorg.conf 

This disables AGP , maybe the card is getting underutilized..i presume .. but its failsafe :)

---

### Post by Stanislav Valasek on 2006-07-11
> **jvictor said:**
> I blacklisted amd64_agp , agpgart
and had to enable SBA and Fastwrites to prevent crashing.

Hi,

I have the same problem, see [my post]("http://www.ubuntuforums.org/showthread.php?t=194128").

Could you please post here steps which helped you? I suppouse, that you blasklisted kernel modules. Could you describe which config files did you edidit and how? Thaks
Stano

---

