---
title: "install new ATi drivers?"
date: 2006-06-03
forum: Desktop Environments
---

### Post by Perfex on 2006-06-03
Well I am trying to install new ATi drivers and I am a bit new to linux, so I downloaded ati-driver-installer-8.25.18-x86.run, then I did the Generate Distribution Specific Driver Package Option, then it made a bunch of packages see [this screenshot]("http://www.imageshell.eu/links/generate-distribution-specific-driver") , how do I install these, I have not a clue, or which one do I install?

Thank you in advance

---

### Post by Rackerz on 2006-06-03
Unfortunately I cannot see that screenshot. PHP error. 

I suggest installing these packages instead from Synaptic. 'fglrx-control' and xorg-driver-fglrx'. 

Then you will need to do this;

First you will need open up your xorg.conf, do this by opening a terminal and typing;
```
sudo gedit /etc/X11/xorg.conf
```

Then you need to go to this line in the file;
> Section "Device"
Under that line you will see 'Driver "ati"' change it to;
```
fglrx
```

Then reboot. (IMPORTANT).

---

### Post by Perfex on 2006-06-03
[QUOTE=Rackerz]Unfortunately I cannot see that screenshot. PHP error. 

I suggest installing these packages instead from Synaptic. 'fglrx-control' and xorg-driver-fglrx'. 

Then you will need to do this;

First you will need open up your xorg.conf, do this by opening a terminal and typing;
```
sudo gedit /etc/X11/xorg.conf
```

Then you need to go to this line in the file;

Under that line you will see 'Driver "ati"' change it to;
```
fglrx
```

Then reboot. (IMPORTANT).[/QUOTE]

did that, ```
under glxinfo -l -v | more
``` I get this.
Seems the driver is not working? direct rendering: No

EDIT - well when I went to install thoese packages from the synaptic it showed they were in but the line that had to be changed was not there, well I went to see if I could uninstall then reinstall to see if that would help the problem, well they will not uninstall, seems the driver is not there, since I was following the ATi readme to remove the file, but the synaptic said it is installed

```
robert@24-179-176-119:~$ glxinfo -l -v | more
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
```

url to screenshot [http://www.imageshell.eu/links/generate-distribution-specific-driver/](http://www.imageshell.eu/links/generate-distribution-specific-driver/)

Names of files that were created with generate Distribution Specific Driver Package Option:

fglrx-control_8.25.18-1_i386.deb
fglrx-kernel-source_8.25.18-1_i386.deb
fglrx-sources_8.25.18-1_i386.deb
xorg-driver-fglrx_8.25.18-1_i386.deb
xorg-driver-fglrx-dev_8.25.18-1_i386.deb
fglrx-installer_8.25.18-1_i386.changes

---

### Post by plaz42 on 2006-06-03
Check this thread:
[http://www.ubuntuforums.org/showthread.php?t=167168](http://www.ubuntuforums.org/showthread.php?t=167168)

Your fglrx issues sound similar to some of the problems there.

---

