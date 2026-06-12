---
title: "display detect &amp; driver problem ATI Radeon 4350  Ubuntu 10.10"
date: 2010-12-20
forum: Desktop Environments
---

### Post by clickbelow on 2010-12-20
the original display drivers were so so until I messed it up (yet another noobish noob)
Version Ubuntu 10.10 64bit
Environment:
Duel Boot Ubuntu / Windows 7
Hardware:
Acer Aspire AX5810
Quad core 4GB ram
Video onboard (no upgrade slot!) ATI Radeon 4350 HD 512MB
Monitors (left via HDMI) 32 inch Samsung TV, 23 inch Samsung Monitor

Initial problems.. Detected TV as 7" monitor  23" ok
Unable to display entire screen on TV, unable to move desktop menus to 23"
No options or advanced options for displays available, able to detect monitors.
Able to reduce TV display setting to show entire screen.

Current problems:
Unable to detect monitors at all stuck in mirrored display mode, edge of TV desktop is off screen.  Tells me to relog to no effect.
Reboots dont help
Deleted xorg.conf & attempted reconfigure.. failed.. tried to mv old xorg.conf and permission was denied (think I did as SUDO)
Reinstalled driver by installing additional drivers

Goal:
Display desktop on right monitor (DVI output)
Display TV at full HDMI on left as work area (drag between)

1.  How can I get it able to detect monitors again?
2.  How do I tell it the TV is not 7"
3.  How do I fix the poor driver problem.


Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
    SubSection "Display"
        Virtual    3840 1080
    EndSubSection
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "fglrx"
EndSection

---

### Post by PhantmKllr on 2010-12-20
Here's the link to the official AMD driver for Linux. [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English")

---

### Post by clickbelow on 2010-12-22
Thanks, tried that, unable to install the driver.
Noticed the instructions appear to be for Windows users & the PC has an Intel Core 2 sticker so am not certain this is what I need.
Under Windows 7 in "Steam" it automatically detected a better GPU driver available & prompted I should update, this would appear to be the same thing (Catalyst) & it was a downgrade disallowing the TV to display fully.. the original driver once again was preferable.

---

### Post by PhantmKllr on 2010-12-22
So you're saying that you can't uninstall the Ubuntu provided drivers?

---

### Post by clickbelow on 2010-12-23
dont believe so.. I'm saying the original Ubuntu driver was better than my current config & that when I downloaded the driver you suggested I am too much of a noob to know what I was supposed to do with it (ie double clicking on it & dragging into terminal didn't work)  & that I am doubtful that it is the driver I need due to the Intel stamp on the outside of the box.. then again being a noob I dont nessecarily know what I am talking about.. if I knew how in the meantime to get back to the original driver (without a reinstall) I would have done it already as it was preferable to mirror screens

make any sense?

if you can tell me step by step how to post reports of hardware data needed by all means do so & ill be happy to apply my noobness to the problem lest problem reside less between chair & keyboard

Managed to get the driver installed.. worse.. the originally installed default ubuntu driver was better

---

### Post by PhantmKllr on 2010-12-23
> **clickbelow said:**
> Managed to get the driver installed.. worse.. the originally installed default ubuntu driver was better

So are you saying that you managed to install the drivers from the ATI Website? And the Ubuntu drivers are better? Hmm. I'm not entirely sure what the problem is here, I don't remember having this much trouble with my ATI card. I have noticed that a lot of people have been having problems with recent HD ATI cards.

I suggest that you switch back to the Ubuntu provided drivers if you can.

---

### Post by clickbelow on 2010-12-24
I'd have to agree but unsure how to go about it hopefully a fix happens in the not too distant future.

---

