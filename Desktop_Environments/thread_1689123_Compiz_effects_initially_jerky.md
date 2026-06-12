---
title: "Compiz effects initially jerky"
date: 2011-02-16
forum: Desktop Environments
---

### Post by kevpatts on 2011-02-16
Hey everyone,

I'm loving my compiz effects on my desktop. Have changed it to run at 60Hz and looks lovely.

One thing I've noticed is that the effects are jerky at first if they haven't been used in a while, but then smoothen in a second or two. Is this because it has to load the background or something?

I have a desktop cylinder with an animated skydome. When I start rotating it it's jerky, but once I've rotated it for about 1 second it goes really smooth. Same with window maximize/minimise effects.

How can I make it smooth from the start?

Kevpatts

---

### Post by kn0w-b1nary on 2011-02-16
this is just a guess... how "nice" is the compiz process?

---

### Post by kevpatts on 2011-02-16
> **kn0w-b1nary said:**
> this is just a guess... how "nice" is the compiz process?

I don't know what you mean. Is there a "niceness" setting in CCSM? In Appearance dialog it's set to Custom (because I've got simple-ccsm installed).

---

### Post by kn0w-b1nary on 2011-02-16
hit ```
Alt+F2
```

and type in: ```
gnome-system-monitor
```

then click on "processes" and there will be a column that says "nice"

---

### Post by kevpatts on 2011-02-16
Ah! It's Nice is 0.

---

### Post by kn0w-b1nary on 2011-02-16
Right-click on the compiz process and select "Change Priority...". Then drag the slider to the left until the nice is -5. Then click "Change Priority".

---

### Post by impact on 2011-02-16
I have noticed that, too. I run Ubuntu on a notebook with C2D cpu and nvidia graphics card. The machine attempts to save power by downclocking both the CPU and the GPU when it's idle. 

When compiz effects are on, it usually takes a second or two for the machine to detect it and switch the GPU to higher frequency. That's what causes the initial jerkiness. After that, everything is smooth until effects stops. When the machine detects that no effects are active, the GPU is no longer required to do any hard work and gets downclocked. 

System - Administration - NVIDIA X Server Settings - Powermizer shows the changes in frequency. You can also use it to force "prefer maximum performance" instead of "adaptive" mode, but that will probably drain your battery faster and generated excess heat. But your transitions will be smoother. :)

---

### Post by kevpatts on 2011-02-17
That seems to have fixed it! Thanks.

---

### Post by kn0w-b1nary on 2011-02-17
Glad it's working!

---

### Post by kevpatts on 2011-02-17
It's not quite working. This setting resets on every reboot. Thread about it here: [http://ubuntuforums.org/showthread.php?p=10467693](http://ubuntuforums.org/showthread.php?p=10467693)

---

### Post by impact on 2011-02-17
I have done a bit of searching and it seem you would have to edit xorg.conf and append a line there. But I haven't tried it.

How-to video:

[http://www.youtube.com/watch?v=_NSJx3G9-zc](http://www.youtube.com/watch?v=_NSJx3G9-zc)

Some more information:

[http://owened.net/2008/04/23/how-to-force-nvidia-powermizer-performance-in-linux](http://owened.net/2008/04/23/how-to-force-nvidia-powermizer-performance-in-linux)

Explanation of parameters (read this first before you edit anything!):

[http://tutanhamon.com.ua/technovodstvo/NVIDIA-UNIX-driver/#power-saving](http://tutanhamon.com.ua/technovodstvo/NVIDIA-UNIX-driver/#power-saving)

[I]Configuration examples
Look at four popular 'RegistryDwords' option values:

    * on battery - max power saving, on AC - max performance

          "PowerMizerEnable=0x1; PerfLevelSrc=0x2222; PowerMizerDefault=0x3; PowerMizerDefaultAC=0x1"

    * on battery - max power saving, on AC - adaptive strategy (my favorite)

          "PowerMizerEnable=0x1; PerfLevelSrc=0x2233; PowerMizerDefault=0x3"

    * on battery - adaptive strategy, on AC - max performance

          "PowerMizerEnable=0x1; PerfLevelSrc=0x3322; PowerMizerDefaultAC=0x1"

    * adaptive strategy for any power source

          "PowerMizerEnable=0x1; PerfLevelSrc=0x3333"

[/I]

---

### Post by kevpatts on 2011-02-24
Works for me. I just added:```
    Option         "NoLogo" "True"
    Option         "RegistryDWords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2222; PowerMizerDefault=0x3; PowerMizerDefaultAC=0x1"
```into the "Device" section and it's fixed it. The setting util still says it's in Adaptive mode though, but I'm pretty sure it's not.

---

