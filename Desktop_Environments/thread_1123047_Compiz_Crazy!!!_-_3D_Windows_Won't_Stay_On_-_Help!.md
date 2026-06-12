---
title: "Compiz Crazy!!! - 3D Windows Won't Stay On - Help!"
date: 2009-04-11
forum: Desktop Environments
---

### Post by Daddyo-613 on 2009-04-11
**CCSM is driving my crazy!** I can't get the 3D Windows effect to work unless I ...

1. go to...System>Preferences>CompizConfig Settings Manager>Preferences>Plugin List

2. disable "Automatic Plugin Sorting" by unchecking the box;

3. locate 3d in the "Disabled Plugins List" and move it to the "Enabled Plugins List".

The trouble is that this setting doesn't survive a reboot or reactivation of the **Automatic Plugin Sorting** of the CCSM **Plugin List**. It's driving me crazy. 
It may not be a long trip but I'd still like to figure out what's going wrong.  

**Here's some spec's on my system:**
CPU:                      Intel Core 2 Duo E6300 1.86GHz(1066MHz) s775
RAM:                      Kingston 1GB 240-pin DDR II 533MHz/PC4200
O/S:                       Ubuntu 8.10 \n \l
Kernel: 2.6.27.11-Generic
Video Card:            Asus GF7300LE w/TurboCache128MB TVOut DVI
Video Driver:          nVidia ver. 180
Settings Manager:   CCSM ver. 0.7.8
Window Manager:    Compiz
Window Decoratior: GTK Window Decorator

I should have plenty of capacity to run the 3D Windows effect.

I've installed all updates current to April 18, 2009. I've switched other CCSM effects on and off and they work fine. The 3D Window effect can still only be activated manually by opening CCSM, going to **Preferences** and disabling **Automatic Plugin Sorting** tab and adding the effect to the list of enabled plugins. Even then this temporary fix is lost on reboot.

I've tried moving the 3d effect up in the loading order but it didn't make any difference. There must be a conflict somewhere or I'm missing an installed dependency but I haven't been able to find it. I've been searching threads and Google for more than a week now and I've found nothing helpful. I can't believe that I'm the only one on the planet who has experienced this problem.

When I run $ compiz  in a terminal this is what I get:

```
stephen@stephen-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: 
/usr/bin/compiz.real (core) - Error: dlsym: /home/stephen/.compiz/plugins/libatlantis.so: undefined symbol: getCompPluginInfo20070830


```then it just hangs and I have to kill the terminal.

Obviously something's not where it should be but I don't know what to look at next. Some help might save my sanity!

---

### Post by Daddyo-613 on 2009-04-12
**Compiz conflict Solved.** It looks like my sanity will be preserved after all. Using Back Trace, I was able to follow the sequence of the file references back from the compiz command to a directory that contained an earlier version of compiz extra plugins. Because those plugins had been installed separately, they had not been removed by the upgrade. The result was that after the upgrade to Intrepid there were two calls for the same plugins and  one of those plugins was the 3D Cube effect.

When the 3D effect was manually activated by turning off the **Automatic Plugin Sorting** feature in CCSM and then manually moved to the active  **Plugin List** the library listing was not used so the plugin worked, When the **Automatic Plugin Sorting** feature was turned back on the corrupted library listing came into play and the effect couldn't run anymore.

By tracing the double reference back to the original files and by deleting the original files and the reference to  them in the lib file and then by uninstalling both the original plugin files and the compiz files and then reinstalling the required compiz files the conflicts were resolved and all the effects work fine.

I have not listed the particular files and directories that had to be removed and reinstalled as their location and content would likely vary from machine to machine and therefore wouldn't be helpful,

I do recommend installing Back Trace as a very useful tool to diagnose problem installations. You may find this wiki helpful: 

[https://wiki.ubuntu.com/DebuggingProgramCrash](https://wiki.ubuntu.com/DebuggingProgramCrash). 

Good Hunting!

---

