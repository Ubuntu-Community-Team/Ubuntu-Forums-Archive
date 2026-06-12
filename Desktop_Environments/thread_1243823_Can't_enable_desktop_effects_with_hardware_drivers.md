---
title: "Can't enable desktop effects with hardware drivers"
date: 2009-08-18
forum: Desktop Environments
---

### Post by aaron424 on 2009-08-18
I can't enable desktop effects anymore. I had them running on this same system, a GF9500 GT, but now that I installed windows 7 and reinstalled ubuntu 9.04 64 bit, it wont work, it just says desktop effects could not be enabled. I have the latest proprietary drivers. This is what the terminal output says:
```
aaron@aaron-desktop:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x1024) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
/usr/share/themes/exotic/gtk-2.0/gtkrc:89: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/exotic/gtk-2.0/gtkrc:90: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/usr/share/themes/exotic/gtk-2.0/gtkrc:156: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.

```

---

### Post by dagrump on 2009-08-18
Try to open Nvidia settings, I'd bet it will tell you that you don't appear to be using nvidia drivers.
If that's the case, you should open the terminal and type,
sudo nvidia-xconfig, then log out & back in or reboot.
Then try to enable the effects.

---

### Post by aaron424 on 2009-08-19
```
aaron@aaron-desktop:~$ sudo nvidia-xconfig
[sudo] password for aaron: 

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: No Layout specified, constructing implicit layout section using screen
         "Default Screen".


WARNING: Unable to find CorePointer in X configuration; attempting to add new
         CorePointer section.


WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: Unable to find CoreKeyboard in X configuration; attempting to add new
         CoreKeyboard section.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

aaron@aaron-desktop:~$ 
```

---

