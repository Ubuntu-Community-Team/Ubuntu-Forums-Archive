---
title: "Xubuntu 14.04 Still screen tearing..."
date: 2015-09-03
forum: Desktop Environments
---

### Post by LastHylian on 2015-09-03
I've tried many suggestions from various threads to get rid of this tearing including using different drivers and using a different compositor. Currently, the best results are with Compton, but the video below still shows the tearing I am seeing.

Xfce4 - Xubuntu 14.04
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.3 LTS
Release:	        14.04
Codename:	trusty


```
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1288 (rev a1)

  *-display               
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:44 memory:f6000000-f6ffffff memory:e8000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
```

Compton Config

~$ compton --backend glx --paint-on-overlay --glx-no-stencil --glx-no-rebind-pixmap --vsync opengl-swc --detect-client-opacity --shadow-exclude "! name~=''" --config ~/.compton.conf -b &

```
backend = "glx";
paint-on-overlay = true;
glx-no-stencil = true;
glx-no-rebind-pixmap = true;
vsync = "opengl-swc"; 

# These are important. The first one enables the opengl backend. The last one is the vsync method. Depending on the driver you might need to use a different method.
# The other options are smaller performance tweaks that work well in most cases. 
# You can find the rest of the options here: https://github.com/chjj/compton/wiki/perf-guide, and here: https://github.com/chjj/compton/wiki/vsync-guide

# Shadow
shadow = true; # Enabled client-side shadows on windows.
no-dock-shadow = true; # Avoid drawing shadows on dock/panel windows.
no-dnd-shadow = true; # Don't draw shadows on DND windows.
clear-shadow = true; # Zero the part of the shadow's mask behind the window (experimental).
shadow-radius = 7; # The blur radius for shadows. (default 12)
shadow-offset-x = -7; # The left offset for shadows. (default -15)
shadow-offset-y = -7; # The top offset for shadows. (default -15)
shadow-exclude = [ "n:e:Notification", "n:e:Docky", "g:e:Synapse", "g:e:Conky", "n:w:*Firefox*", "n:w:*Chromium*", "class_g ?= 'Notify-osd'", "class_g ?= 'Cairo-dock'", "class_g ?= 'Xfce4-notifyd'", "class_g ?= 'Xfce4-power-manager'"];

# Fading
fading = true; # Fade windows during opacity changes.
fade-delta = 4; # The time between steps in a fade in milliseconds. (default 10).
fade-in-step = 0.03; # Opacity change between steps while fading in. (default 0.028).
fade-out-step = 0.03; # Opacity change between steps while fading out. (default 0.03).
#no-fading-openclose = true; # Fade windows in/out when opening/closing

# Window type settings
wintypes:
{
  tooltip = { fade = true; shadow = false; };
};
```

Video footage of my tearing
[https://www.youtube.com/watch?v=jfSBpnLaq08]("https://www.youtube.com/watch?v=jfSBpnLaq08")

Test video can be found here : [https://www.youtube.com/watch?v=cuXsupMuik4](https://www.youtube.com/watch?v=cuXsupMuik4)

---

### Post by v3.xx on 2015-09-03
Did this include the 355 driver?

[http://ubuntuforums.org/showthread.php?t=2293066&p=13349318&viewfull=1#post13349318](http://ubuntuforums.org/showthread.php?t=2293066&p=13349318&viewfull=1#post13349318)

---

### Post by LastHylian on 2015-09-04
Unfortunately, yes. As you can see, it is incredibly noticeable. 
Using Chromium Version 44.0.2403.89 Ubuntu 14.04 (64-bit) with HTML5 YouTube Videos, however, this happens with a local file played through VLC as well.


[IMG]http://i.imgur.com/lT89iNh.png[/IMG]

---

### Post by jeremy9856 on 2015-09-04
The tearing with the Nvidia proprietary drivers on Xfce has been fixed ([http://git.xfce.org/xfce/xfwm4/commit/?id=8a67212860898ef02fee79f64fc774bc14ed769c](http://git.xfce.org/xfce/xfwm4/commit/?id=8a67212860898ef02fee79f64fc774bc14ed769c)).
The fix is not included in Xubuntu or a PPA for now so you have to compile Xfwm4. I explain how to do that here, it's simple : [http://ubuntuforums.org/showthread.php?t=2287998&p=13349439#post13349439](http://ubuntuforums.org/showthread.php?t=2287998&p=13349439#post13349439)

---

