---
title: "Compiz got error after install Mac4lin"
date: 2009-08-06
forum: Desktop Environments
---

### Post by pushxor on 2009-08-06
Hi, My compiz-fusion in Ubuntu 9.04 got error after instal Mac4lin, the top bar n button disapper n can't click.

My spec: Intel Core2Dudo T5550 1,83 Ghz, 4GB ram, Intel X3100 vga

 Result of compiz-check

```
uwing@whocare:~$ chmod +x compiz-check  
 uwing@whocare:~$ ./compiz-check  
 

 Gathering information about your system...  
 

  Distribution:          Ubuntu 9.04  
  Desktop environment:   GNOME  
  Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)  
  Driver in use:         intel  
  Rendering method:      AIGLX  
 

 Checking if it's possible to run Compiz on your system...  
 

  Checking for texture_from_pixmap...               [ OK ]  
  Checking for non power of two support...          [ OK ]  
  Checking for composite extension...               [ OK ]  
  Checking for FBConfig...                          [ OK ]  
  Checking for hardware/setup problems...           [ OK ]  
 

 uwing@whocare:~$  
 
```compiz-check

```
uwing@whocare:~$ compiz -check  
 Checking for Xgl: not present.  
 xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log  
 Detected PCI ID for VGA:  
 Checking for texture_from_pixmap: not present.  
 Trying again with indirect rendering:  
 Checking for texture_from_pixmap: present.  
 Checking for non power of two support: present.  
 Checking for Composite extension: present.  
 Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.  
 Checking for Software Rasterizer: Not present.  
 Checking for nVidia: not present.  
 Checking for FBConfig: present.  
 running under gnome seesion, checking for gnomecompat  
 Checking for Xgl: not present.  
 /usr/bin/compiz.real (core) - Warn: Unknown option '-check'  
 

 /usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"  
 /usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0  
 metacity: Unknown option -check  
 uwing@whocare:~$  
 
```my xorg.conf file

```
#sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
Option "AccelMethod" "UXA" Option "MigrationHeuristic" "greedy"

EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```Thanks for your help :popcorn:

---

### Post by stumbleUpon on 2009-08-06
Mac4Lin enables Metacity compositing and so compiz does not work.

First disable compositing in Metacity:
Alt + F2. Type gconf-editor. Navigate to apps > metacity > general. Uncheck compositing_manager option.

Then enable compiz as usual in the Appearences > Visual Effects tab.


If you want to use both Mac4Lin and compiz, then during the installation of Mac4Lin you should say 'no' to enabling metacity compositing option. You can use compiz for that. Just reinstall Mac4Lin and dont enable metacity compositing.

---

### Post by harry71194 on 2009-10-19
> **stumbleUpon said:**
> Mac4Lin enables Metacity compositing and so compiz does not work.

First disable compositing in Metacity:
Alt + F2. Type gconf-editor. Navigate to apps > metacity > general. Uncheck compositing_manager option.

Then enable compiz as usual in the Appearences > Visual Effects tab.


If you want to use both Mac4Lin and compiz, then during the installation of Mac4Lin you should say 'no' to enabling metacity compositing option. You can use compiz for that. Just reinstall Mac4Lin and dont enable metacity compositing.
Thank you very much! I installed Mac4Lin, then ended up hating it, but then couldn't find out how to remove the compiz-like stuff afterwards, even after apt-get autoremoving it. <3

---

