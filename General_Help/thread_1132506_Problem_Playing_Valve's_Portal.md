---
title: "Problem Playing Valve's Portal"
date: 2009-04-21
forum: General Help
---

### Post by Flexico on 2009-04-21
I know other people have posted about this, but none of those threads helped me.

I have Steam and Portal successfully installed, but Portal's graphics barely show up. (see screenshot, that was the title screen)

My graphics card may just not be up to the task, but I did manage to play Portal on this computer with Windows XP, so I don't know.

:KS

---

### Post by lovinglinux on 2009-04-22
I have installed Steam and Portal today and it plays. It's much more laggy then running on Windows, but it works. Maybe your gfc barely meets the requirements to allow you to play on Windows, but won't play on Wine. Just guessing.

---

### Post by skymera on 2009-04-22
What is your graphics card?

---

### Post by Flexico on 2009-04-22
> **skymera said:**
> What is your graphics card?

I don't know the exact specs. How do I find that?

---

### Post by lovinglinux on 2009-04-22
Since you don't know which card you have, then you probably have a on-board card. So that is probably the issue.

To find out, run the following command:

```
lshw
```

Then look for something like this:

```
           *-display
                description: VGA compatible controller
                product: G70 [GeForce 7300 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
```

I have manged to get Portal running without lagging. Maybe this could fix your problem. Here are the steps:

Open Steam, right-click the "Portal" game in the "My Games" tab, then select properties, then click "Set launch options", then add *-dxlevel 81*

Works great now!

---

### Post by Flexico on 2009-04-22
> **lovinglinux said:**
> 
I have manged to get Portal running without lagging. Maybe this could fix your problem. Here are the steps:

Open Steam, right-click the "Portal" game in the "My Games" tab, then select properties, then click "Set launch options", then add *-dxlevel 81*

Works great now!

Excellent, thank you! What exactly did the code do? The graphics seem a bit glitchy now, did it disable some features?

---

### Post by lovinglinux on 2009-04-23
> **Flexico said:**
> Excellent, thank you! What exactly did the code do? The graphics seem a bit glitchy now, did it disable some features?

Great news. 

The code tells the game to run using DirectX 8.1 instead of 9.0c.

Portal is one of the best game I ever played. Unfortunately it becomes boring after finishing all levels. If you have the full version, you can try playing the [Prelude mod](http://www.portalprelude.com/).

BTW, what version of Wine do you have? If you installed the version from the repository, then you might get a better result installing the latest release. I'm running 1.1.19

---

### Post by Flexico on 2009-04-23
I have the Prelude and level packs "the flash version" and "maybe black mesa". =D

I think I got wine by doing "apt-get install wine" in the terminal. I'm on my Mom's computer right now so I can't check my version.

---

