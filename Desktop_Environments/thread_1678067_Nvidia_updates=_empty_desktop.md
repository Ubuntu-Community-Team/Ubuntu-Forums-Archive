---
title: "Nvidia updates= empty desktop"
date: 2011-01-29
forum: Desktop Environments
---

### Post by Rogar on 2011-01-29
Ubuntu 10.04, gnome, nvidia 7000 series card. Recent kernel and nvidia updates caused this situation. I boot to a login selector,like normal. When I login I get my bootup sound and background, but no panels. Right clicking does nothing. I booted up a puppylinux cd, deleted xorg.conf, and can now get to a working desktop. I have, through the additional drivers utility, deleted and reinstalled nvidia current driver. Twice. No change. Windows XP (On another hard drive) works well, so it's not a card problem. Has anyone had this problem?

---

### Post by gordintoronto on 2011-01-29
You get "a working desktop," followed by "no change." I can't figure out what problem you are referring to.

By the way, to identify your video card, run Accessories/Terminal:
lspci | grep VGA

There are literally hundreds of Nvidia 7000 series cards. But they aren't all the same.

---

### Post by Rogar on 2011-01-29
I get a working desktop if I delete xorg.conf and reboot. That means I am not using nvidia drivers for the session.

---

### Post by gordintoronto on 2011-01-30
> **Rogar said:**
> I get a working desktop if I delete xorg.conf and reboot. That means I am not using nvidia drivers for the session.

I'm pretty sure that is not true. If you run "additional drivers" I think you will see that you're using the Nvidia driver.

By default, there is no xorg.conf.

---

### Post by Krytarik on 2011-01-31
> **gordintoronto said:**
> I'm pretty sure that is not true. If you run "additional drivers" I think you will see that you're using the Nvidia driver.

By default, there is no xorg.conf.
Sorry, I have to give *Rogar* right, the "nvidia" driver must be set in xorg.conf to get run at the launch of a xserver.

But you are of course right in saying that there is no xorg.conf by default.

@Rogar: Set up your xorg.conf for the nvidia driver again, with the following options:
```
sudo nvidia-xconfig --add-argb-glx-visuals --no-logo --force-generate
```This adds the following option to the "Screen" section, I need to have it there, although it is said to be enabled by default:
```
Option         "AddARGBGLXVisuals" "True"
```If that doesn't fix the issue, you may try the PPA of Ubuntu-X-Swat, to get the most recent driver:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Rogar on 2011-01-31
Thanks for understanding, Krytarik. I will give it a try when I get the chance. I'm also going to try logging in as another user.

---

### Post by Rogar on 2011-01-31
I had no luck when trying the last suggestion. I have tried logging in as another user. I have tried a lcd monitor in place of the usual crt monitor (and rebuilding the xorg.conf with the nvidia-config command. I always get an empty, unresponsive desktop. I already had the xswat ppa enabled. It seems that nvidia drivers inhibit the booting process of the desktop. Thanks anyway for the suggestions.

---

### Post by Krytarik on 2011-01-31
Check "~/.xsession-errors" and "/var/log/Xorg.0.log", respectively "/var/log/Xorg.0.log.old" for error messages.

Check if the monitor specs (hopefully) included in your xorg.conf are correct:
```
sudo apt-get hwinfo
hwinfo --monitor
```
or (press "Cancel")
```
xvidtune
```
My "Monitor" section looks like this:
```
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Sony CPD-4401"
    HorizSync       30.0 - 107.0
    VertRefresh     48.0 - 120.0
    Option         "DPMS"
EndSection
```

---

### Post by gordintoronto on 2011-01-31
> **Krytarik said:**
> Sorry, I have to give *Rogar* right, the "nvidia" driver must be set in xorg.conf to get run at the launch of a xserver.


I don't know where you get that idea. There is no xorg.conf on my computer, but it uses an Nvidia driver.

---

### Post by Krytarik on 2011-01-31
> **gordintoronto said:**
> I don't know where you get that idea. There is no xorg.conf on my computer, but it uses an Nvidia driver.
Have you done anything special to set the nvidia driver? How did you install it?

---

### Post by Rogar on 2011-02-01
After uninstalling all traces of compiz, and writing a minimal xorg.conf file (only the device section), I have my nvidia display again. I will mark this as solved, but I'm not sure that computing is possible without wobbly windows. Woe is me.

---

### Post by gordintoronto on 2011-02-01
> **Krytarik said:**
> Have you done anything special to set the nvidia driver? How did you install it?

I ran Administration/Additional Drivers.

---

### Post by Krytarik on 2011-02-01
> **gordintoronto said:**
> I ran Administration/Additional Drivers.
I'm curious what the output of the following command is:
```
lshw -c video
```

@Rogar: Sorry, that you chose to give up that fast.

---

### Post by gordintoronto on 2011-02-02
description: VGA compatible controller
       product: G96 [GeForce 9400 GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:18 memory:fa000000-faffffff memory:d0000000-dfffffff memory:f8000000-f9ffffff ioport:ef00(size=128) memory:fb000000-fb07ffff

---

### Post by Krytarik on 2011-02-02
> **gordintoronto said:**
> description: VGA compatible controller
       product: G96 [GeForce 9400 GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:18 memory:fa000000-faffffff memory:d0000000-dfffffff memory:f8000000-f9ffffff ioport:ef00(size=128) memory:fb000000-fb07ffff
So, obviously the nvidia driver is somehow run, but that's definetely not the default behaviour.

---

