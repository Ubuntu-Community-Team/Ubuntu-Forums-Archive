---
title: "Console Resolution Conundrum"
date: 2020-05-18
forum: Desktop Environments
---

### Post by watchpocket on 2020-05-18
When I switch from the X-window-system GUI to the console (by hitting Ctl-Alt-F3), what displays there is a huge, unwieldy fontsize at a very low-rez. For days now I have been searching for a way to change the console resolution to a higher setting to make its font smaller and more clear.  

(Or for a way to at least set the font itself to a smaller size, without trying to change resolution).

And I don't think, at least in my case, that it's just a matter of changing some of the settings in ***/etc/default/grub***.  Because I have tried all manner of settings in that file according to advice from various blogs, tutorials and ask-ubuntu question/answers.  (Yes, I *update-grub2 && shutdown -r now *after every settings change.)

It may in fact be necessary to make certain changes in /etc/default/grub, but I think ***some*** other factor(s) must be involved. 

*Here's what gets me:*  I know that my system is capable of displaying a higher resolution in the console because when I boot from a live-USB, the higher-rez and smaller font immediately display in the console before the hand-off to X. 

Given that a higher rez is clearly possible in my console, what -- or with what combination of settings in which locations -- should I be looking at to try to set it permanently?

I'm running Ubuntu-MATE 18.04.4 on a desktop workstation. Here is some of my system info from inxi:
```
[COLOR=#0000ff]System:[/COLOR]    Kernel: 5.3.0-51-generic x86_64 [COLOR=#0000ff]bits:[/COLOR] 64 [COLOR=#0000ff]compiler:[/COLOR] gcc v: 7.5.0 [COLOR=#0000ff]Desktop:[/COLOR] MATE 1.20.1 
           [COLOR=#0000ff]Distro:[/COLOR] Ubuntu 18.04.4 LTS (Bionic Beaver)
 
[COLOR=#0000ff]Machine:[/COLOR]   [COLOR=#0000ff]Type: [/COLOR]Desktop System: System76 [COLOR=#0000ff]product:[/COLOR] Wild Dog Performance[COLOR=#0000ff] v: [/COLOR]wilp6 [COLOR=#0000ff]serial:[/COLOR] <filter> 
           [COLOR=#0000ff]Mobo: [/COLOR]Intel [COLOR=#0000ff]model:[/COLOR] DP45SG v: AAE27733-405 [COLOR=#0000ff]serial: [/COLOR]<filter>[COLOR=#0000ff] BIOS:[/COLOR] Intel v: SGP4510H.86A.0108.2009.0114.2036 
          [COLOR=#0000ff] date:[/COLOR] 01/14/2009 

[COLOR=#0000ff]CPU:       Topology: [/COLOR]Quad Core [COLOR=#0000ff]model:[/COLOR] Intel Core2 Quad Q9650 [COLOR=#0000ff]bits:[/COLOR] 64 [COLOR=#0000ff]type:[/COLOR] MCP [COLOR=#0000ff]arch:[/COLOR] Penryn [COLOR=#0000ff]rev: [/COLOR]A L2 cache: 6144 KiB 
           [COLOR=#0000ff]flags:[/COLOR] lm nx pae sse sse2 sse3 sse4_1 ssse3 vmx [COLOR=#0000ff]bogomips:[/COLOR] 23999 
           [COLOR=#0000ff]Speed:[/COLOR] 2000 MHz [COLOR=#0000ff]min/max: [/COLOR]1998/2997 MHz [COLOR=#0000ff]Core speeds (MHz): 1: [/COLOR]2000 [COLOR=#0000ff]2:[/COLOR] 2000[COLOR=#0000ff] 3:[/COLOR] 2000 [COLOR=#0000ff]4:[/COLOR] 2000
 
[COLOR=#0000ff]Graphics:  Device-1: [/COLOR]NVIDIA GF106 [GeForce GTS 450] [COLOR=#0000ff]driver: [/COLOR]nvidia[COLOR=#0000ff] v: [/COLOR]390.132 [COLOR=#0000ff]bus ID:[/COLOR] 01:00.0 
          [COLOR=#0000ff] Display: [/COLOR]x11 [COLOR=#0000ff]server: [/COLOR]X.Org 1.20.5 [COLOR=#0000ff]driver: [/COLOR]nvidia [COLOR=#0000ff]unloaded:[/COLOR] fbdev,modesetting,nouveau,vesa 
           [COLOR=#0000ff]resolution: 1:[/COLOR] 2560x1600~60Hz [COLOR=#0000ff]2: [/COLOR]2560x1600~60Hz
```

---

### Post by CatKiller on 2020-05-18
> **watchpocket said:**
> *Here's what gets me:*  I know that my system is capable of displaying a higher resolution in the console because when I boot from a live-USB, the higher-rez and smaller font immediately displays in the console before the hand-off to X. 

When you're using the live image, you're using nouveau rather than the Nvidia proprietary driver. Because it's open source (like the AMD and Intel drivers) nouveau plays nicely with others, but it doesn't have much performance. The proprietary driver has the performance but doesn't play nicely with others.

You can use KMS (kernel mode setting) with the proprietary driver if your install is in UEFI mode. If it's in BIOS mode you're limited to old crusty methods that likely won't make all modes available - just whatever's exposed by VBE. KMS support was a work-in-progress for quite a while with the proprietary driver: I don't know where the driver you're using with that old card falls in that process.

I've got 2560×1600 TTYs with my Nvidia card by having
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nvidia-drm.modeset=1"

GRUB_GFXMODE=2560x1600x32,1920x1080x32,auto
```

in my /etc/default/grub.

---

### Post by watchpocket on 2020-05-18
> **CatKiller said:**
> You can use KMS (kernel mode setting) with the proprietary driver if your install is in UEFI mode. If it's in BIOS mode you're limited to old crusty methods that likely won't make all modes available - just whatever's exposed by VBE. KMS support was a work-in-progress for quite a while with the proprietary driver: I don't know where the driver you're using with that old card falls in that process.

Aha! My Ubuntu-MATE 18.04 install ***is ***in fact in BIOS mode (and this is almost certainly the source of the problem), but I am about to install MATE 20.04 on a separate internal SSD, and I plan to do that in UEFI mode, since I just discovered that my BIOS has a setting to enable "UEFI boot," which I enabled.

However, I've read that both install-modes should be the same: both should be either UEFI or legacy BIOS.   (Though I don't know if this is the case if the installs are on separate drives.) So I most likely will plan on changing the 18.04 install from BIOS to UEFI *before *I install 20.04.  

I *think* my graphics card was the newest that my box (which dates from 2009) could acommodate.  But I may be able to update the card's nvidia driver, and I'll look into that. At that point perhaps, with UEFI OS installs and an updated graphics driver, I can get better console resolution.  I had no idea that nouveau was being used with a live-USB, so thanks for clearing that up.  Meanwhile freaking damn all proprietary software!

---

### Post by CatKiller on 2020-05-19
> **watchpocket said:**
> However, I've read that both install-modes should be the same: both should be either UEFI or legacy BIOS.   (Though I don't know if this is the case if the installs are on separate drives.) So I most likely will plan on changing the 18.04 install from BIOS to UEFI *before *I install 20.04.

Yep, still the case even if they're on separate drives. The whole boot process and how the hardware is accessed is different between the two, as well as the change from MBR to GPT. I haven't tried the changing from one to the other, although I understand that it's possible. My last remaining BIOS install will be getting a fresh UEFI install of 20.04 when I get round to it.

---

