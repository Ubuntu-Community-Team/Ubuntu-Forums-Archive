---
title: "Poor gaming performance"
date: 2021-02-03
forum: Gaming &amp; Leisure
---

### Post by somir on 2021-02-03
I'm using Ubuntu 20.04.2 LTS with GNOME 3.36.8, just installed it today.

I haven't installed many things, I wanted to try playing CS:GO and see how it goes.

Before, in Win10 it worked just fine. I had a good framerate and it was playable with Low settings.

The first time I tried in Ubuntu, it crashed. I started it again and set the absolute minimum settings and tried again, after a long loading screen I got into the game.

It was unplayable; It stabilized a little later but it was still very laggy. What can I do to fix this?

--INFO--

I'm using the nvidia-340 driver instead of the open source noveau drivers;

PC specs:

Intel Core i3 530 2.93 GHz (2 cores, 4 threads)
Nvidia GeForce GTS 250
2TB HDD
4GB DDR3 RAM

---

### Post by QIII on 2021-02-03
Moved to Gaming & Leisure for a better fit.

---

### Post by mastablasta on 2021-03-06
didn't see this one. if you are still arround....
> **somir said:**
> I'm using Ubuntu 20.04.2 LTS with GNOME 3.36.8, just installed it today.

--INFO--

I'm using the nvidia-340 driver instead of the open source noveau drivers;


make sure they are being actually utilized/used. it think last to support 340 will be 20.04.1, but i could be wrong.
> 
PC specs:

Intel Core i3 530 2.93 GHz (2 cores, 4 threads)
Nvidia GeForce GTS 250
2TB HDD
4GB DDR3 RAM

nvidia doesn't support the default Wayland well. so be sure to change it to xorg. hopefully that will help to improve performance.

i have single core Athlon, 4 Gb ram and GT730. game runs well on medium. but since last update it takes 8 minutes to load to menu and then 2 minutes for the map to load. i have my dinner in between. after it loads it works well.
this is not limited to old PC as my kid has Ryzen 7 with 16 Gb ram and GTX 1650  and the game still loads a lot slower than it did before. for him it is close to 2 minutes now. the other one has Ryzen 5 with 8GB ram and fast nvme drive - before he loaded in few seconds now it takes him a while to get into menu. i haven't figured out what is causing the slow loads yet. maybe the next update will resolve it.

you can try:
- disabling videos on load with -novid launch parameter
- removing videos and background animation by renaming videos folder in panorama (but it seems to not be as effective since last update)

---

### Post by nunchuckmadness on 2021-03-06
> **somir said:**
> 

Intel Core i3 530 2.93 GHz (2 cores, 4 threads)
Nvidia GeForce GTS 250
2TB HDD
4GB DDR3 RAM

you need more robust hardware, at least a gt1030 to play on low settings, and more ram would help.

---

### Post by CelticWarrior on 2021-03-06
> **nunchuckmadness said:**
> you need more robust hardware, at least a gt1030 to play on low settings, and more ram would help.
Granted, they do need better hardware for gaming, any gaming, but saying they need "at least a GT1030 to play on low settings" is utterly ridiculous.

CS:GO system requirements (Linux):
```

[LIST]
[*][COLOR=#61686D][FONT=Arial]OS:[/FONT][/COLOR] Ubuntu 12.04
[*][COLOR=#61686D][FONT=Arial]Processor:[/FONT][/COLOR] 64-bit Dual core from Intel or AMD at 2.8 GHz
[*][COLOR=#61686D][FONT=Arial]Memory:[/FONT][/COLOR] 4 GB RAM
[*][COLOR=#61686D][FONT=Arial]Graphics:[/FONT][/COLOR] nVidia GeForce 8600/9600GT, ATI/AMD Radeon HD2600/3600 (Graphic Drivers: nVidia 310, AMD 12.11), OpenGL 2.1
[*][COLOR=#61686D][FONT=Arial]Storage:[/FONT][/COLOR] 15 GB available space
[*][COLOR=#61686D][FONT=Arial]Sound Card:[/FONT][/COLOR] OpenAL Compatible Sound Card
[/LIST]

```

And, for comparison, the system requirements for Windows:
```

[LIST]
[*][COLOR=#61686D][FONT=Arial]OS:[/FONT][/COLOR] Windows® 7/Vista/XP
[*][COLOR=#61686D][FONT=Arial]Processor:[/FONT][/COLOR] Intel® Core&#8482; 2 Duo E6600 or AMD Phenom&#8482; X3 8750 processor or better
[*][COLOR=#61686D][FONT=Arial]Memory:[/FONT][/COLOR] 2 GB RAM
[*][COLOR=#61686D][FONT=Arial]Graphics:[/FONT][/COLOR] Video card must be 256 MB or more and should be a DirectX 9-compatible with support for Pixel Shader 3.0
[*][COLOR=#61686D][FONT=Arial]DirectX:[/FONT][/COLOR] Version 9.0c
[*][COLOR=#61686D][FONT=Arial]Storage:[/FONT][/COLOR] 15 GB available space
[/LIST]

```

Source: [https://store.steampowered.com/app/730/CounterStrike_Global_Offensive/](https://store.steampowered.com/app/730/CounterStrike_Global_Offensive/)

So, one thing is now clear: The system requirements for Linux are notably higher which means the game has been highly optimized for the proprietary Microsoft's DirectX. That it runs better in Windows using the same barely enough hardware is therefore no surprise. The old and not-gaming-oriented GTS250 is the main bottleneck here.

---

### Post by nunchuckmadness on 2021-03-07
> **CelticWarrior said:**
> Granted, they do need better hardware for gaming, any gaming, but saying they need "at least a GT1030 to play on low settings" is utterly ridiculous.

welp, probably in windows, he is using a 1gb card in 2017. [URL="https://www.youtube.com/watch?v=z3ebql5V_0U"]https://www.youtube.com/watch?v=z3ebql5V_0U

[/URL]

---

### Post by CelticWarrior on 2021-03-07
> **nunchuckmadness said:**
> welp, probably in windows, he is using a 1gb card in 2017. [URL="https://www.youtube.com/watch?v=z3ebql5V_0U"]https://www.youtube.com/watch?v=z3ebql5V_0U

[/URL]

And an older but much better CPU, double the RAM and much faster and, of course, Windows.
In a nutshell, the Youtuber's hardware would be reasonable for the game in Linux and the OP's barely enough for the same game in Windows. But you can't expect miracles with the OP's hardware in Linux for any DirectX optimized game in Linux with OpenGL.

---

