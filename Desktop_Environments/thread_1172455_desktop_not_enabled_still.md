---
title: "desktop not enabled still"
date: 2009-05-28
forum: Desktop Environments
---

### Post by mrdancemachine on 2009-05-28
Hey there everyone and I still can't install compiz to get it to work and has anyone found a work around to fix this issue...

Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1440x900) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator


Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV44A [GeForce 6200] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

tony@ubuntu:~$ Gathering information about your system...
bash: Gathering: command not found
tony@ubuntu:~$ 
tony@ubuntu:~$  Distribution:          Ubuntu 9.04
bash: Distribution:: command not found
tony@ubuntu:~$  Desktop environment:   GNOME
bash: Desktop: command not found
tony@ubuntu:~$  Graphics chip:         nVidia Corporation NV44A [GeForce 6200] (rev a1)
bash: syntax error near unexpected token `('
tony@ubuntu:~$  Driver in use:         nvidia
bash: Driver: command not found
tony@ubuntu:~$  Rendering method:      Nvidia
bash: Rendering: command not found
tony@ubuntu:~$ 
tony@ubuntu:~$ Checking if it's possible to run Compiz on your system...
> 
>  Checking for texture_from_pixmap...               [ OK ]
>  Checking for non power of two support...          [ OK ]
>  Checking for composite extension...               [ OK ]
>  Checking for FBConfig...                          [ OK ]
>  Checking for hardware/setup problems...           [ OK ]
> 


Ok i have it installed but it will not work.... Help or ideas anyone? [http://ubuntuforums.org/images/smilies/icon_confused.gif:?:?:?:?:?:?:?](http://ubuntuforums.org/images/smilies/icon_confused.gif:?:?:?:?:?:?:?)

---

### Post by Tibuda on 2009-05-28
What is this output? How are you trying to install compiz? I thought it was installed by default on Ubuntu.

---

### Post by mrdancemachine on 2009-05-28
When i installed the new version Compiz is not installed by default and i looked for it first. Then i searched the forums and this lead me to this link--> [http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion) so far it is installed but the desktop is still not enabled.

---

### Post by mrdancemachine on 2009-05-28
ok i got it figured out and it was the compiz settings manager was not installed to begin with.. case closed on my end.. :p:KS

---

