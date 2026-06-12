---
title: "Login screen never displaying in Ubuntu 18.04, can't access TTY either"
date: 2019-11-08
forum: Desktop Environments
---

### Post by robroseknows on 2019-11-08
[COLOR=#242729][FONT=Arial]I've been dealing with this for [a couple days now]("https://askubuntu.com/questions/1185577/boot-halts-or-display-doesnt-work-on-ubuntu-18-04"), but I think I've narrowed it down to a display issue rather than the boot as a whole halting, because the computer remains on and logs show boot continues despite lack of display. I cannot enter TTY mode[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Currently my computer shows the BIOS splash and then a purple screen, but after a few seconds, the display stops and the monitor enters power saving mode without any sort of login screen ever displaying. This isn't a new install, and I don't know what could've caused it to stop working. I've been on 18.04 for like a year now without issue. I can enter recovery mode, but nothing I've done in it has helped. I am using a Ryzen processor, nVME SSD and NVIDIA GPU with proprietary drivers.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]What I've tried already:[/FONT][/COLOR]

[LIST]
[*]Switching quiet splash to nomodeset, no change.
[*]Uncommenting WaylandEnabled=False in gdm3 config, no change.
[*]Switching to lightdm from gdm, no change.
[*]Updating packages while in recovery mode, no change.
[*][This fix]("https://askubuntu.com/a/760935/487048") by installing nvidia drivers in recovery mode, no change.
[/LIST]
[COLOR=#242729][FONT=Arial]I can provide logs other than those in the old post, just let me know which ones would be helpful. I'm really at my wits end.[/FONT][/COLOR]

---

### Post by mörgæs on 2019-11-10
Hi, welcome to the fora.

Ryzen is the latest breed of AMD processors and it deserves the latest software. How does 19.10 behave?

---

### Post by CatKiller on 2019-11-10
This is the issue:

```
] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    12.042] (==) NVIDIA(0):     will be used as the requested mode.
[    12.042] (==) NVIDIA(0): 
[    12.042] (--) NVIDIA(0): No enabled display devices found; starting anyway because
[    12.042] (--) NVIDIA(0):     AllowEmptyInitialConfiguration is enabled
[    12.042] (II) NVIDIA(0): Validated MetaModes:
[    12.042] (II) NVIDIA(0):     "NULL"
[    12.042] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[    12.042] (WW) NVIDIA(0): Unable to get display device for DPI computation.
```

Your computer is not getting the information from your display about the resolutions it can do, so it's defaulting to 640×480, which your monitor can't do.

The version of the driver you're using, 430.50, isn't one that comes from the PPA, and you've got a bunch of things being loaded - nouveau, vesa, and so on - that can mess things up and are blacklisted by the install scripts when you install from the package, so I suspect you've used the .run file from the Nvidia site. That is generally a complete pain to manage.

You also haven't said how your display is connected to your machine, and whether it's going through any kind of adaptor that would mess with EDID. 

My advice would be to check your cabling, and get rid of the driver installed by the .run file, and install the driver from the graphics driver PPA.

You also said that you get a purple screen, which means you installed Ubuntu in BIOS mode rather than UEFI. That's not the best idea with a modern machine. For your next install it would be best to install it in UEFI mode.

---

### Post by rbmorse on 2019-11-10
> **CatKiller said:**
> 
You also said that you get a purple screen, which means you installed Ubuntu in BIOS mode rather than UEFI. That's not the best idea with a modern machine. For your next install it would be best to install it in UEFI mode.

Not necessarily.  I get the purple screen on my UEFI install as the first screen after GRUB selection menu. This usually clears after a couple seconds and the iPL continues on to blank the display.  Sometimes power saving on the display activates, sometimes not. The login screen appears within about 2 seconds.  Usually. 

Occasionally, however, I experience the same symptoms as the OP.  Usually the first boot of the day after the machine has been off for several hours.  The process either stalls on the purple screen or when the display blanks just afterwards. I'm using the nvidia driver package 430.35 from repository as installed by the "additional drivers" utility. 

I can confirm Ubuntu installed in the UEFI mode as evidenced by efibootmgr and rEFInd both operating correctly and the presence of /sys/firmware/efi. 

I agree with your diagnosis that the driver isn't receiving EDID data from the display. 

OP: It sounds like the EDID module in your display failed.  This is not unusual. If the problem persists _after_ performing all the checks/steps suggested by catkiller (including removing the existing nvidia driver and replacing it with the appropriate driver package for your display adapter from repository), I'd try a different display and cable.  Use the display port connectors and cable if possible as this seems to be the most reliable method. 

But first, the longshot:  Try power cycling the display after all hard drive activity ceases (mostly) on the bootup.

---

