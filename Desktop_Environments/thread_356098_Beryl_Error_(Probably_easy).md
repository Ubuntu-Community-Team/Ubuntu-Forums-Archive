---
title: "Beryl Error (Probably easy)"
date: 2007-02-08
forum: Desktop Environments
---

### Post by Meshuggah27 on 2007-02-08
I had beryl working fine,  Then it randomly stopped working and i got this error.  I tried reinstalling it too.

> mesh@mesh-laptop:~$ beryl-manager
mesh@mesh-laptop:~$ **************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension


Someone help! :(

---

### Post by Waappu on 2007-02-08
Hi

Add these lines end of /etc/X11/xorg.conf file if you don't have those already

first type in terminal
```
gksudo gedit /etc/X11/xorg.conf
```
then add end of file and save
```
Section "Extensions"
	Option		"Composite" "Enable"
EndSection
```

---

### Post by Meshuggah27 on 2007-02-08
I uninstalled the fglrx drivers and went to the ATI site and installed the ones there

Now when i start beryl i get

> **************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Checking for non power of two texture support   : failed

Support for non power of two textures missing
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

(emerald-theme-manager:8519): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.


My god this is annoying -_-

BTW I have a ATI Radeon 9600 Mobile

---

### Post by ser1alsn1per on 2007-02-08
use xgl insetead

---

