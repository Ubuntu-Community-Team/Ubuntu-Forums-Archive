---
title: "one screen brighter than the other..."
date: 2005-07-07
forum: Desktop Environments
---

### Post by gammyhand on 2005-07-07
I finally got dual screen desktop working (as one huge desktop) and find that one screen is brighter than the other (both with the same monitor settings on brightness/contrast). I know the problem is not hardware as I swapped the ports over and whichever monitor is on DVI output has the problem (although the dvi output goes to an analogue adapter so both monitors receive an analogue signal).

When I used windows XP I did not have this problem, maybe it had some in built metering?

Is there a way to fix this?

---

### Post by Lunde on 2005-07-07
[QUOTE=gammyhand]I finally got dual screen desktop working (as one huge desktop) and find that one screen is brighter than the other (both with the same monitor settings on brightness/contrast). I know the problem is not hardware as I swapped the ports over and whichever monitor is on DVI output has the problem (although the dvi output goes to an analogue adapter so both monitors receive an analogue signal).

When I used windows XP I did not have this problem, maybe it had some in built metering?

Is there a way to fix this?[/QUOTE]
 If you have a Nvidia card, the the nvidia-settings can correct the problem.
[http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)

$ sudo apt-get nvidia-settings (But read the above link)

---

### Post by gammyhand on 2005-07-07
[QUOTE=Lunde]If you have a Nvidia card, the the nvidia-settings can correct the problem.
[http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)

$ sudo apt-get nvidia-settings (But read the above link)[/QUOTE]
 Nope, an ati radeon 9800pro :(

---

### Post by jrobcet on 2005-07-07
I think you can do some gamma adjustment to individual screens through the ATI control panel. You can install it with apt:```
sudo apt-get install fglrx-control
```

Once you have it installed it can be started with the "fireglcontrol" command.

Of course, all this assumes you have the ATI drivers properly installed.

---

### Post by gammyhand on 2005-07-07
[QUOTE=jrobcet]I think you can do some gamma adjustment to individual screens through the ATI control panel. You can install it with apt:```
sudo apt-get install fglrx-control
```

Once you have it installed it can be started with the "fireglcontrol" command.

Of course, all this assumes you have the ATI drivers properly installed.[/QUOTE]
 I have already played with the gamma on there. It does not seem to help. I guess I will have to try and be more accurate with it :)

---

### Post by jrobcet on 2005-07-07
[QUOTE=gammyhand]I have already played with the gamma on there. It does not seem to help. I guess I will have to try and be more accurate with it :)[/QUOTE]Of course if all alse fails you should be able make the adjustments on the monitors themselves.

---

### Post by shakin on 2005-07-07
This is a driver problem, but you can probably correct it with the xorg gamma settings.

In the "Monitor" section for the monitor you want to change the gamma on you can add this:

Gamma .8 .8 .8

That will set your gamma to .8 of normal. Change the values to whatever you want. You can also adjust the colors by making the RGB values different.

---

### Post by gammyhand on 2005-07-07
[QUOTE=shakin]This is a driver problem, but you can probably correct it with the xorg gamma settings.

In the "Monitor" section for the monitor you want to change the gamma on you can add this:

Gamma .8 .8 .8

That will set your gamma to .8 of normal. Change the values to whatever you want. You can also adjust the colors by making the RGB values different.[/QUOTE]
 For which monitor shakin? It's only one with the problem. And how do you know that .8 .8 .8 will be right?

Is it possible to set the exact screen resolution? Under windows xp my screens looked best at 60hz but they have set themselves to 75hz in  linux (they support both modes). I want to try setting it to 60hz for both of them.

---

### Post by gammyhand on 2005-07-21
[QUOTE=gammyhand]For which monitor shakin? It's only one with the problem. And how do you know that .8 .8 .8 will be right?

Is it possible to set the exact screen resolution? Under windows xp my screens looked best at 60hz but they have set themselves to 75hz in  linux (they support both modes). I want to try setting it to 60hz for both of them.[/QUOTE]
 Anyone know the answer?

---

