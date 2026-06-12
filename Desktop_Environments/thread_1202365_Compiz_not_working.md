---
title: "Compiz not working"
date: 2009-07-02
forum: Desktop Environments
---

### Post by Phantom Hoover on 2009-07-02
When I try to activate Compiz, it dumps the following and refuses to work:
```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1366x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```It worked fine before, so how can I fix it?

EDIT: It has fixed itself, leaving me no nearer to finding out the cause.

EDIT 2: It's stopped again

---

### Post by Linux Kelley on 2009-07-02
Mine was working fine until yesterday and now I can only get it to work by entering the [COLOR="Red"]Compiz[/COLOR] command in terminal.

Here is the result.

[COLOR="Blue"]kelley@kelley-ubuntu-desktop:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1920x1200) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.[/COLOR]


Thank you for any help.

Kelley

Ubuntu 9.04 64 bit

---

### Post by Linux Kelley on 2009-07-02
Just as I posted this it failed again.

Here is the failure.

[COLOR="Blue"]^CSegmentation fault[/COLOR]

Kelley

---

