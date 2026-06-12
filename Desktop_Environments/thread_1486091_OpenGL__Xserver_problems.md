---
title: "OpenGL / Xserver problems"
date: 2010-05-17
forum: Desktop Environments
---

### Post by ONEother on 2010-05-17
Installed Kubuntu 10.04 on my brand new laptop, got everything working except for certain programs that rely on OpenGL.  The weird thing is that the other computer I was using (Ubuntu) after updating from 9.10 had the same problem, but very recently 'fixed itself', probably during a standard update.
When trying to run something that runs on opengl (i.e. alien arena), I get this error message:
```
------- sound initialization -------
dlopen() on libopenal.so.1 failed
Sound failed: Unable to start OpenAL.
Game will continue without sound.
--------- [Loading Renderer] ---------
Initializing OpenGL display
...setting mode 3: 1024 768
Using XFree86-VidModeExtension Version 2.2
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  17
  Current serial number in output stream:  17
```

The important part being "X error of failed request".

xorg.conf follows:
```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:2:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

Assistance is greatly appreciated!

---

### Post by ONEother on 2010-05-20
I've narrowed it down to this: fgrlx-amdccle can't find fglrx in the right spot.  When I attempt to resolve those dependencies (apt-get, aptitude, or adept), I get this error
```
Unpacking fglrx (from .../fglrx_2%3a8.723.1-0ubuntu3_amd64.deb) ...
updateStatus( 'fglrx', 'half-installed', ''), seen = 14/60

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

dpkg: error processing /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu3_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
updateStatus( '/var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu3_amd64.deb ', 'error ', 'subprocess new pre-installation script returned error exit status 1'), seen = 15/60
updateStatus( 'fglrx', 'config-files', ''), seen = 16/60

```

So apparently fglrx isn't installing correctly for some reason.

---

### Post by ONEother on 2010-05-20
I'm a total double poster...

So I followed directions [here]("http://ubuntuforums.org/showthread.php?t=1456282") and it seemed to install properly.  New error message!

```
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  65 (X_PolyLine)
  Serial number of failed request:  15
  Current serial number in output stream:  18

```

Now I realize this isn't a high priority thread, but it seems awfully empty right about now... *cricket* :(

---

