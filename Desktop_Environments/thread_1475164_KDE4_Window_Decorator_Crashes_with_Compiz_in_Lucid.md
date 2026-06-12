---
title: "KDE4 Window Decorator Crashes with Compiz in Lucid Lynx 10.04"
date: 2010-05-06
forum: Desktop Environments
---

### Post by PJSingh5000 on 2010-05-06
This is a thread to discuss Bug #572780 - KDE Window Decorator crash using Compiz in Kubuntu 10.04 Lucid Lynx.

ACTIONS:
On Kubuntu x64 10.04 Lucid Lynx, install the following Compiz packages...
    compiz
    compizconfig-settings-manager
    compiz-kde
    compiz-fusion-plugins-main
    compiz-fusion-plugins-extra
    fusion-icon

Select Compiz as the window manager. KDE Window Decorator crashes with the following error...

RESULT:
Application: KDE Window Decorator (kde4-window-decorator), signal: Segmentation fault

POSSIBLE WORK-AROUND:
Use the Plastik window decoration theme...

Select K | System Settings | Appearance | Windows | Window Decoration (tab)
Select "Plastik" from the drop down.
Click Apply button.

---

### Post by PJSingh5000 on 2010-05-06
Has anyone else had success with the Plastik approach?  (One user in the bug report said it did not work for him).

I have tried this on three machines.
Two are Intel x64 with on-board Intel graphics chips.
One is AMD x64 with an older ATI graphics card.

The trick worked on all machines, but I did start off with a fresh install of Kubuntu 10.04, instead of an upgrade.

---

### Post by kastel on 2010-05-07
I am the one for whom the trick did not work. Instead, the X server crashed immediately.

However, I'm using Openbox now, hopefully waiting for compiz-kde packet to be updated, as the problem has already been fixed upstream.

Cheers.

---

### Post by kastel on 2010-05-07
Edit: the trick works now. What caused X to crash was the transition from Openbox to Compiz.

---

### Post by BryanFRitt on 2010-05-17
The Plastik setting for Window Decoration trick worked for me.

--

possible confusion for those who are sleepy...

K menu -> Application -> Settings -> System Settings -> Look & Feel section -> Appearance -> **Windows** -> Window Decoration Tab -> Plas_**tik**_, is not the same as 
K menu -> Application -> Settings -> System Settings -> Look & Feel section -> Appearance -> **Style** -> Applications tab -> Widget style, which has a setting called 'plas_**tique**_'

---

### Post by Zorael on 2010-05-18
The kde-window-decorator decorator has basically always been garbage in KDE4, so I've used Emerald instead. It can't use normal KDE4 decorations, but [kde-look.org](http://kde-look.org/index.php?xcontentmode=102) has some decent themes to pick from.

---

### Post by texaswriter on 2010-06-07
> **Zorael said:**
> The kde-window-decorator decorator has basically always been garbage in KDE4, so I've used Emerald instead. It can't use normal KDE4 decorations, but [kde-look.org](http://kde-look.org/index.php?xcontentmode=102) has some decent themes to pick from.

This worked for me. 

```

sudo aptitude install emerald libemeraldengine0
compiz --replace
emerald --replace

```

Good luck.

---

### Post by cneha on 2010-06-10
> **texaswriter said:**
> This worked for me. 

```

sudo aptitude install emerald libemeraldengine0
compiz --replace
emerald --replace

```Good luck.

when i run these command,while executing the command compiz --replace my system stopped working and i had to restart.i am using KDE 10.04.and i selected window decorator as emerald still i am unable to install theme.
any help??

---

### Post by texaswriter on 2010-06-10
Supposing Kwin is currently running: Install emerald and its prerequisites as well as compiz

Then compiz --replace; emerald --replace; 

That didn't stop my system. If it does, ensure *which* one is freezing it. Does using one halt your system or the other... Or in other words, try them by themselves. Emerald may not [probably won't] use the same theme that was installed by itself. You can google emerald theme download and find suitable themes.

---

### Post by oneye on 2010-10-01
> **PJSingh5000 said:**
> Has anyone else had success with the Plastik approach?  (One user in the bug report said it did not work for him).

I have tried this on three machines.
Two are Intel x64 with on-board Intel graphics chips.
One is AMD x64 with an older ATI graphics card.

The trick worked on all machines, but I did start off with a fresh install of Kubuntu 10.04, instead of an upgrade.

Switching to Plastic allowed Compiz to use the KDE Window Manager without any error.

I'm running 10.04 x64 on a Asus G73JH (ATI Mobility Radeon HD 5870 & Intel i7) 
I had Compiz up & running with Emerald Window Manger working fine but read somewhere that support for Emerald may be dropped (or something like that). So I thought I would try switching the Window Decorator to KDE4 via the Compiz Fusion Icon. At first this worked without any errors popping up but there were no borders around my windows. I tried to apply a new style under System Settings>Appearance>Style with no change. But after I went into Compiz Config Settings Manager - Effects>Window Decoration, under command I removed the --replace from 'kde4-window-decorator --replace' & once I reloaded my Window Manager that error popped up (still with no Window Borders of course). I set So I went back to Emerald.

TLDR; Plastic Fix worked for me. Sounds like the Compiz crew have a fix already in the works.

-1i

---

### Post by lorebett on 2010-10-08
Hi
is there a way to turn on/off compiz from a kde configuration menu? or is the command line the only approach?
thanks in advance
Lore

---

