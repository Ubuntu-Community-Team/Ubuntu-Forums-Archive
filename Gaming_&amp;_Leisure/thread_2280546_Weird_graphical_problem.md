---
title: "Weird graphical problem"
date: 2015-05-31
forum: Gaming &amp; Leisure
---

### Post by remi3 on 2015-05-31
Hi, this is my first post on this forum.
Usually i find everything already posted and answered but with this problem I can't find anything.

With every game i play I get this weird pixels flashing on my screen, from games i've installed from Ubuntu Software Center to games from Steam.
I think it has something to do with the drivers from my graphical card but i don't seem to have any other drivers i can install.
I need you expertise guys.

Thanks in advance

---

### Post by mactrent2 on 2015-05-31
remi3,  If you could provide a bit more information on your hardware, that might call to mind a known issue.  There are better ways to find out this information, but I would find out your specs by running the following as root: ```
lspci -vnn | grep VGA -A 12
``` Before posting back, though I'd check for proprietary drivers for your card in the Software & Updates tool's Addition Drivers tab.  If that turns up nothing, you can search for your card's specs and see if anybody has the same problems.  A cursory DuckDuckGo search offers pretty much the same advice, without the command for getting details: [https://www.linux.com/news/hardware/drivers/8203-is-my-hardware-linux-compatible-find-out-here](https://www.linux.com/news/hardware/drivers/8203-is-my-hardware-linux-compatible-find-out-here)  Happy to see you in the GNU/Linux community, and Ubuntu in particular!  Best of luck, and don't forget to let future 'net generations know how this turns out! -Mactrent  Edit for tech specs report:  The following information under "PCI devices" should serve as a basis for further searches. ```
VGA compatible controller		: NVIDIA Corporation GK107 [GeForce GTX 650] (rev a1) (prog-if 00 [VGA controller])
``` Also, seeing only "Unknown" under the OpenGL section is not a good sign.  Looks like proprietary drivers will be your best bet if you haven't already tried the specifically NVidia-compatible drivers from the Nouveau project ([http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/)).

---

### Post by efflandt on 2015-06-02
What desktop are you running, because default Ubuntu under Operating System would usually show something like```
-Version-
Kernel        : Linux 3.13.0-53-generic (x86_64)
Compiled        : #89-Ubuntu SMP Wed May 20 10:34:39 UTC 2015
C Library        : Unknown
Default C Compiler        : GNU C Compiler version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) 
Distribution        : Ubuntu 14.04.2 LTS
-Current Session-
Computer Name        : XPS-8100-1404
User Name        : efflandt (David Efflandt)
Home Directory        : /home/efflandt
Desktop Environment        : Unity (ubuntu)
-Misc-
Uptime        : 5 hours, 22 minutes
Load Average        : 0.18, 0.13, 0.08
```Not sure what the OpenGL things show for default nouveau driver, but I would think that **nvidia-331-updates** package should work for GTX 650, since it worked for my GTX 550 Ti that I had before. The easiest way to install specific packages is to install **synaptic** using **Ubuntu Software Center** and then put **nvidia** in Quick search. But first hit the swirly arrow in synaptic to update software sources.

I am actually using a newer driver from a ppa repository, but at the bottom of the Display section it shows this:```
-OpenGL-
Vendor        : NVIDIA Corporation
Renderer        : GeForce GTX 750 Ti/PCIe/SSE2
Version        : 4.5.0 NVIDIA 352.09
Direct Rendering        : Yes
```

---

### Post by remi3 on 2015-06-07
> **mactrent2 said:**
> remi3,  If you could provide a bit more information on your hardware, that might call to mind a known issue.  There are better ways to find out this information, but I would find out your specs by running the following as root: ```
lspci -vnn | grep VGA -A 12
``` Before posting back, though I'd check for proprietary drivers for your card in the Software & Updates tool's Addition Drivers tab.  If that turns up nothing, you can search for your card's specs and see if anybody has the same problems.  A cursory DuckDuckGo search offers pretty much the same advice, without the command for getting details: [https://www.linux.com/news/hardware/drivers/8203-is-my-hardware-linux-compatible-find-out-here](https://www.linux.com/news/hardware/drivers/8203-is-my-hardware-linux-compatible-find-out-here)  Happy to see you in the GNU/Linux community, and Ubuntu in particular!  Best of luck, and don't forget to let future 'net generations know how this turns out! -Mactrent  Edit for tech specs report:  The following information under "PCI devices" should serve as a basis for further searches. ```
VGA compatible controller        : NVIDIA Corporation GK107 [GeForce GTX 650] (rev a1) (prog-if 00 [VGA controller])
``` Also, seeing only "Unknown" under the OpenGL section is not a good sign.  Looks like proprietary drivers will be your best bet if you haven't already tried the specifically NVidia-compatible drivers from the Nouveau project ([http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/)).

Sorry for this late answer.
I have no updates available, and this is what i get when i run the code.

```
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK107 [GeForce GTX 650] [10de:0fc6] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:2802]
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    Expansion ROM at f7000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau

01:00.1 Audio device [0403]: NVIDIA Corporation GK107 HDMI Audio Controller [10de:0e1b] (rev a1)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:2802]

```

---

### Post by remi3 on 2015-06-07
> **efflandt said:**
> but I would think that **nvidia-331-updates** package should work for GTX 650, since it worked for my GTX 550 Ti that I had before. The easiest way to install specific packages is to install **synaptic** using **Ubuntu Software Center** and then put **nvidia** in Quick search. But first hit the swirly arrow in synaptic to update software sources.



SOLVED!

This worked for me, thanks alot for your help its much appriciated. :)
I have not yet tested it on any other games but i think it will be fine if not i'll post back here.

[ATTACH=CONFIG]262474[/ATTACH]

---

