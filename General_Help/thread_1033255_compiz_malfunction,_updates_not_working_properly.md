---
title: "compiz malfunction, updates not working properly"
date: 2009-01-07
forum: General Help
---

### Post by Cayal on 2009-01-07
I decided to reboot this morning due to unresponsive google desklets. When I reboot, I was reduced to 2 virtual desktops and no desktop effects, including beryl and compositing. Trying to enable them from Appearance preferences yields "searching for available drivers" before telling me desktop effects could not be enabled. Running compiz from terminal gives me:
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 
/home/cayal/.themes/&#1008;/gtk-2.0/gtkrc:98: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/cayal/.themes/&#1008;/gtk-2.0/gtkrc:103: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/home/cayal/.themes/&#1008;/gtk-2.0/gtkrc:109: Murrine configuration option "style" is not supported and will be ignored.
/home/cayal/.themes/&#1008;/gtk-2.0/gtkrc:152: Murrine configuration option "style" is not supported and will be ignored.
/home/cayal/.themes/&#1008;/gtk-2.0/gtkrc:285: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/cayal/.themes/&#1008;/gtk-2.0/gtkrc:348: error: invalid string constant "murrine-menu-bar", expected valid string constant

```
I'm not using any proprietary drivers, I don't think the Murrine engine is causing this, do I need xgl? If so, how do I install it? 

[COLOR="Silver"]In addition, something seems to be awry with my updates, I think it has something to do with cairo-dock, which I installed from the Intrepid repositories with Synaptic before remembering the proper way outlined on the Ubuntu wiki. When I tried to install it normally, I just got errors afer it had done all of the downloading. The update manager now tells me updates are available (and it lists 151 of them, all ranging from kilobytes to megabytes) but tells me the download size is 0 KB. I tried to update last night, I believe the result was some sort of failure.[/COLOR]
EDIT: I think the update problem was nothing, Firefox just told me it was updated, so I assume most of the other critical updates went through as well.

My system is a Lenovo 3000 N200 laptop with a mobile GM965/GL960 integrated graphics controller.

---

### Post by Cayal on 2009-01-07
I ran Forlong's Compiz-Check script and got:
```
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
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


```

What is a software rasterizer and how do I enable/disable/free up this so that desktop effects can run?

EDIT: Well, someone gave me a solution in IRC, thankfully. :)

[Wed Jan 7 2009] [18:06:13] <Slart>	Cayal: some forum threads recommend running this command "sudo dpkg-reconfigure -phigh xserver-xorg"

---

