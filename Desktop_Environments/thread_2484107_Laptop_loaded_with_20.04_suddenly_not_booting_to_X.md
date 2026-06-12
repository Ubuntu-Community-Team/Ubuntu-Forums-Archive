---
title: "Laptop loaded with 20.04 suddenly not booting to Xfce"
date: 2023-02-17
forum: Desktop Environments
---

### Post by mdlueck on 2023-02-17
Greetings,

I have a friend's laptop that several years ago now I reloaded with Xubuntu. Seems to be running 20.04 currently.

It will not boot into Xfce graphics.... gets to:

/dev/sda1: clean, ####/#### files, ####/#### blocks

Then flashes to black screen / then back to the above one line of text.

I booted to root command line, dmsg.log and syslog looked healthy, no complaints of say hardware failure going on.

The Xorg log files were unfortunately empty.

Suggestions to further diagnose what is going on with this system?

I am thankful,

---

### Post by grahammechanical on 2023-02-19
> It will not boot into Xfce graphics.... gets to:

Did it used to load to a login screen and desktop user interface?

> /dev/sda1: clean, ####/#### files, ####/#### blocks

That is standard Linux operating procedure. Next a display manager should load (LightDM?) which in turn should load the login screen. I cannot think of anything more. Except to suggest

Load the Grub boot menu (press Shift on a BIOS motherboard or ESC on a UEFI motherboard) and select an older Linux kernel. Or, a Linux kernel with recovery mode. The Resume option will load to a normal boot but without using a proprietary video driver. Nvida are in the habit of dropping support for its older video adapters. It may be that 20.04 is set to load a proprietary video driver that is not available in 20.04. You may need to switch that machine to open source video drivers.

Regards.

---

### Post by mdlueck on 2023-02-19
> **grahammechanical said:**
> Did it used to load to a login screen and desktop user interface?


Oh yes! Looks like I might have loaded it with 14.04 originally, and LTS upgrades 14.04 --> 16.04 --> 18.04 --> 20.04. I guess this system has been around for a while.


> **grahammechanical said:**
>  The Resume option will load to a normal boot but without using a proprietary video driver. Nvida are in the habit of dropping support for its older video adapters. It may be that 20.04 is set to load a proprietary video driver that is not available in 20.04. You may need to switch that machine to open source video drivers.


The Live DVD of Xubuntu 22.04 loads beautifully on the system. It has integrated ATI graphics.

The client agreed to have me rescue some data files, then reset and load Xubuntu 22.04 fresh.

When it was on 14.04, I had set it to legacy boot mode. This go around, I just switched the BIOS to EFI boot mode.... which Xubuntu 22.04 seems to now prefer over Legacy mode BIOS's.

I found it very difficult to debug / heal busted the X environment.

I am thankful,

---

