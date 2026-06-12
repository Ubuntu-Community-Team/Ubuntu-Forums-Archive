---
title: "Monitor not identified properly!"
date: 2010-12-15
forum: Desktop Environments
---

### Post by rsteinmetz70112 on 2010-12-15
I have a machine with an Nvidia chipset I recently upgraded from 8.04 and switched monitors on it. The new monitor is actually a Polaroid 1511 TLXB high definition TV.

The driver identifies it as a Proview 1511 TLXB. I thought that might be another brand name for the same device but it also apparently misidentifies the available video resolutions.

When I press the info button on the TV remote it displays the input being used (VGA) and the resolution (i.e. 1440x900@60 HZ). These do not generally match the resolutions listed as available for the driver, resulting is a mismatch of the display.

I have identified the following resolutions the monitor is reporting;

    640x480@75
    800x600@75
    832x624@74
    1024x768@75
    1152x864@75
    1280x800@?
    1280x966@60
    1280x1024@75
    1366@768@60
    1440@900@60
    1680@1050@60

I am stuck presently using 1024x768@75Hz as the highest resolution that matches

Using the Nvidia driver can I simply edit xorg.conf? Can I create a specific profile for this monitor to use? If so where can I find out how to do that?

After digging around with cvt and xrandr I was able to add modes that matched close enough, but Ubuntu keeps overiding those settings. Where and how can I add a new monitor?.

---

### Post by Stainesy on 2010-12-15
With the switch to KMS (Kernel Mode Setting) since 10.04 and its automatic detection of graphics many users seem to be having a similar issue with various monitors not detected correctly, and/or Hsync and VertRefresh ranges being incorrect.   These issues often cause KMS to default to Vesa drivers which provide the user with poorer resolution options.  For example I run a Nvidia GeForce GT240 graphics card hooked up to a Samsung SyncMaster 2333 monitor (1920x1080) and neither Ubuntu 10.10 nor LinuxMint 10 could correctly detect the monitor and its settings when using the default Nouveau driver.  The issues were reported in the Xorg.log.  So I purged Nouveau and installed a Nvida driver and now both OS' run as normal.  So do you use the default Nouveau driver, a Nvidia driver or some other?  And check your Xorg.log

---

### Post by rsteinmetz70112 on 2010-12-16
I've used both the Nvidia and Nouveau drivers with differant but not very good results.

Looking around, based on your clue about KMS (Kernel Mode Setting) it is possible to turn KMS off 

[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

I wonder if that gives you back the graphics controls that used to be there or it you're left in to manually configure Xorg.conf. 

I still haven't found out how to add a new monitor type to the configuration.

I'm going to try playing with it when I have a chance.

---

