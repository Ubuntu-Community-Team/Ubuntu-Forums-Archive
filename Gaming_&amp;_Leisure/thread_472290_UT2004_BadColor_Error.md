---
title: "UT2004 BadColor Error"
date: 2007-06-12
forum: Gaming &amp; Leisure
---

### Post by thunderd on 2007-06-12
I am running Ubuntu 7.04 on a P3 nVidia GeForce 2.  When I first install the legacy driver for the video card, ut runs fine, but my max resolution is 800x600.  When I run the following command:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and enable 1280x1024 resolution and reboot, I receive the following error upon startup of ut:
```

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Signal: SIGSEGV [segmentation fault]
Aborting.


Crash information will be saved to your logfile.
X Error of failed request:  BadColor (invalid Colormap parameter)
  Major opcode of failed request:  79 (X_FreeColormap)
  Resource id in failed request:  0x260000c
  Serial number of failed request:  126
  Current serial number in output stream:  128
```

Any suggestions?

---

### Post by Cappy on 2007-06-13
try running
```

sudo nvidia-settings

```
change to the "X Server Display Configuration" tab , setting up your resolution if it is not detected in there, and Clicking "Save to X Configuration File" and reboot.

Post your output from
```

glxinfo | grep render

```
if that doesn't work.

---

### Post by thunderd on 2007-06-13
the command
```
sudo nvidia-settings
```
is not recognized.  Here is the output from glxinfo:
```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

---

### Post by Cappy on 2007-06-13
Your nvidia drivers aren't working.

Try this:
```

sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove
sudo apt-get install nvidia-glx-legacy linux-restricted-modules-`uname -r`

```
(reboot)

I would save that code to a file in your home directory as something like "nvidiainstall.sh" and then
```
chmod +x nvidiainstall.sh
```
(any time before you run it)
then you can run it easily with
```
sudo sh nvidiainstall.sh
```

---

