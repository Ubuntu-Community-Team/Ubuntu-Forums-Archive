---
title: "Window redraws/flicker"
date: 2014-07-28
forum: Desktop Environments
---

### Post by Jane_Bardziev on 2014-07-28
I'm a returning ubuntu user, so beside Windows 7 on my notebook i installed Ubuntu 14.04 LTS.

Notebook:
Dell N5110
CPU i3 2350M
RAM 4 GB
GPU Intel HD3000 & AMD HD6470/7450M

The problem i am facing is that in many programs, the contents "redraw" often causing flicker which is very annoying and tiresome. I do not care for the dedicated GPU, so i'm running only on HD3000 (so i would assume, the outpit of /cat/kernel/debug/vgaswitcheroo/switch) is

```

jane@Dell:~$ sudo cat /sys/kernel/debug/vgaswitcheroo/switch
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :DynOff:0000:01:00.0

```

```

jane@Dell:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series] (rev ff)

```

Here are all Intel related packages. Tried with the built-in Intel drivers, and currently have Intel 1.05 Linux drivers from Intel installed.

```

jane@Dell:~$ dpkg -l | grep "Intel "
ii  i965-va-driver:amd64                                  1.3.0-1ubuntu1                                      amd64        VAAPI driver for Intel G45 & HD Graphics family
ii  intel-gpu-tools                                       1.6-1                                               amd64        tools for debugging the Intel graphics driver
ii  intel-linux-graphics-installer                        1.0.5-0intel1                                       amd64        Intel graphics drivers update utility
ii  libva-intel-vaapi-driver                              1.3.0-1ubuntu1                                      all          VAAPI driver for Intel G45 & HD Graphics family (transitional package)
ii  xserver-xorg-video-intel                              2:2.99.910-0ubuntu1                                 amd64        X.Org X server -- Intel i8xx, i9xx display driver


```

In CompizConfig, have tried all combinations of:
General>OpenGL:
- Framebuffer object
- Vertex Buffer Object (disabling this causes desktop to go black, i can see the launcher bar, but everything else is not displayed)
- Always use buffer swapping

Utility>Workaround:
- Force synchronization of X and GLX

and various other. Have added i915.powersave=0, no change. It's driving me nuts, any advice is welcome.

Edit: It is very noticeable in Firefox and CompizConfig. Pretty much all programs are affected, but these two suffer most...

---

### Post by Jane_Bardziev on 2014-08-01
Anyone else facing this problem, or know something i could try?

I want to note that this was happening from the start, right off from the start on a clean Ubuntu 14.04 LTS installation.

---

### Post by dan167 on 2015-04-21
Same problem,, at times have 50 mouse curors flickering all over the screen :\
Regards Dan
 Ubuntu Noob btw
:P

---

