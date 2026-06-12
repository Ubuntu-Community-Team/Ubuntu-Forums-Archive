---
title: "Compiz fails after plugging in external monitor"
date: 2009-01-04
forum: General Help
---

### Post by johnnyloot on 2009-01-04
Hi all,
I'm running Intrepid on a Dell Inspiron 640M which has an Intel GMA950. I plugged in an external monitor to my laptop and everything was working fine (compiz included). I then removed the external monitor and compiz no longer starts. 
Startup message is as follows:

> 
~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 

I know that XGL is in fact present since Compiz ran correctly previously and I did not installing/removing between now and then. I tried restarting X and no change. 

I am wondering if has to do with the virtual screen resolution which happens when it goes multi-monitor. 

Of course when I try to enable visual effects I get the "Desktop effects could not be started" dialogue.

Any help would be appreciated.

Other of-asked for outputs:
> ~$ sudo lshw -C display
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

> 
~$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 



---

### Post by johnnyloot on 2009-01-04
Running
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

seems to have solved the issue. After a restart, compiz is able to load. It no longer however startup with Ubuntu, but thats an easy fix.

---

### Post by Nuggs on 2009-01-05
Thank you johnnyloot!!!  I had the same problem, and the reconfigure did the trick!

---

