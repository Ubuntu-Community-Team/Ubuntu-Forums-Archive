---
title: "Inspiron E1505N Ubuntu Edition 1280x800 problem"
date: 2007-06-08
forum: Dell  Ubuntu Support
---

### Post by lshlyapnikov on 2007-06-08
Hi everyone!

Want to share how I solved the problem with 1280x800 screen resolution on my brand new Dell Inspiron E1505N Ubuntu Edition laptop.

Got my laptop (happy with it:). Everything worked fine from the box (even the wireless adapter!) except 1280x800 screen resolution in Gnome.

1. Tried to set it through Gnome System panel, the list of available resolutions did not contain 1280x800. The default xorg.conf looked OK and contained all the required settings.

2. Tried to play with/reconfigure xorg.config, it did not help.

Google helped. Found the following information: [http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/) and installed 915resolution Debian package, rolled back to the default xorg.conf from the box. Restarted the laptop and was able to select 1280x800 in the Gnome System Panel Resolutions.

To Dell Support:
I don't know why Dell engineers did not include 915resolution package in the default installation. Without this package  'Intel Integrated Graphics Media Accelerator 950 GM' does not work in X with 1280x800 (at least it did not work on my laptop). 1024x768 looks ugly on a wide screen. This could scare away new Linux users.

Regards,
Leonid Shlyapnikov

---

### Post by stchman on 2007-06-08
> **lshlyapnikov said:**
> Hi everyone!

Want to share how I solved the problem with 1280x800 screen resolution on my brand new Dell Inspiron E1505N Ubuntu Edition laptop.

Got my laptop (happy with it:). Everything worked fine from the box (even the wireless adapter!) except 1280x800 screen resolution in Gnome.

1. Tried to set it through Gnome System panel, the list of available resolutions did not contain 1280x800. The default xorg.conf looked OK and contained all the required settings.

2. Tried to play with/reconfigure xorg.config, it did not help.

Google helped. Found the following information: [http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/) and installed 915resolution Debian package, rolled back to the default xorg.conf from the box. Restarted the laptop and was able to select 1280x800 in the Gnome System Panel Resolutions.

To Dell Support:
I don't know why Dell engineers did not include 915resolution package in the default installation. Without this package  'Intel Integrated Graphics Media Accelerator 950 GM' does not work in X with 1280x800 (at least it did not work on my laptop). 1024x768 looks ugly on a wide screen. This could scare away new Linux users.

Regards,
Leonid Shlyapnikov

Should not have Dell fixed the problem.  I am surprised that it left the facility with the correct res no working.  Does the modem in the laptop work?

The 915 resolution is not needed for the 950GMA.  They should have installed the xserver-xorg-video-intel package.  This enables 3D acceleration and the proper resolution in the 950.  Worked on my girlfriend's laptop.  Google Earth works very well.

---

### Post by benanzo on 2007-06-08
915resolution is needed if you use the i810 Xorg module for the GMA950.  If Dell shipped the system set to default to that module, they should have included the 915resolution package by default.  Otherwise they should have defaulted to the intel module, which solves that problem.  I imagine that they didn't do that (possibly) because they wanted to stay as close to a vanilla Feisty install as possible.

I imagine future revisions will use the intel module to avoid the BIOS patch.

---

### Post by stchman on 2007-06-09
> **benanzo said:**
> 915resolution is needed if you use the i810 Xorg module for the GMA950.  If Dell shipped the system set to default to that module, they should have included the 915resolution package by default.  Otherwise they should have defaulted to the intel module, which solves that problem.  I imagine that they didn't do that (possibly) because they wanted to stay as close to a vanilla Feisty install as possible.

I imagine future revisions will use the intel module to avoid the BIOS patch.

It is not, my girlfriend's  laptop has a 1440x900 resolution and all I had to do was install the xserver-xorg-video-intel package and all was fine.  Her laptop has a 950GMA card.

---

### Post by camarojones on 2007-06-09
Seems to depend on the native resolution of the monitor and what card you have.

The nVidia card and WXGA+ was immediately recognized (1440x900) from a default base installation.
 (Just for those that ordered that setup)

---

### Post by benanzo on 2007-06-11
> It is not, my girlfriend's laptop has a 1440x900 resolution and all I had to do was install the xserver-xorg-video-intel package and all was fine. Her laptop has a 950GMA card.

915resolution is required if you use the default **xserver-xorg-video-i810** module.  You're right that it's *not* required if you use **xserver-xorg-video-intel**.

My point was that if Dell was going to use the **xserver-xorg-video-i810** for the machines with Intel chips, then they should have included **915resolution**.  Otherwise they should have used **xserver-xorg-video-intel** by default.

This will be worked out in future revisions of their systems.

---

