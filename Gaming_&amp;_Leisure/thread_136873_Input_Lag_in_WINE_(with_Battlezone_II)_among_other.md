---
title: "Input Lag in WINE (with Battlezone II) among other things"
date: 2006-02-26
forum: Gaming &amp; Leisure
---

### Post by Zeroangel on 2006-02-26
Hi all,

I am having a few problems getting Windows games working under WINE. The game I want to play is a fairly obscure First Person RTS called 'Battlezone II'.

First of all, I can't seem to launch the game itself. When I launch the main .exe file it says that it cannot find a file that is clearly in the same folder as the bzone.exe file that I am launching the game with. Leading me to believe that it doesn't initialize the folders properly.

I also have a MOD installed with its own executable. Basically what the executable does is swap out some folders before calling the (main) bzone.exe file and launching it. For some reason that works and the MOD is perfectly playable. So if I can't get the main game working I'll just play the MOD.

Anyways, when I do actually play it, I experience a large amount of input lag (as in: it takes half a second for a mouse movement to register), especially when trying to play online (where input lag is very important). The game is fairly old (released in 1998) and uses DirectX7, so I don't think that it would be terribly complicated.

Does anyone know of any tweaks I can make to WINE so that input lag is reduced? and optionally, does anyone know how to get the main game to properly initialize its location?

---

### Post by handy on 2006-02-27
Did you search the forum for any **Battlezone II** content?

I just did a search, nothing there...

The only tweak that I can offer is to add the **CPU Frequency Monitor** to a panel & run your cpu at maximum (**Performance**) speed before you start the (a) game, & then switch back to **OnDemand** when you finish gaming.  This is only useful if your machine has **powernowd** running, i.e. throttling speed up & down to save energy.

I have found that this helps reduce post zoning lag in Guild Wars, but not as much as turning down the graphics detail! :KS

---

### Post by Zeroangel on 2006-02-27
Thanks for the tip!

I couldn't get powernowd running. Says something about my motherboard possibly not supporting temperature readings, even though I just bought (an admittedly generic) AXP/Sempron supporting board.

However, I did manage to get rid of the input lag (purely by chance) by editing my /etc/X11/xorg.conf file for my GeForce4MX card. ```
Section "Device"
        Identifier      "Device[0]"
        Driver          "nvidia"
        BusID           "PCI:2:0:0"
[b]        Option          "NoLogo"
        Option          "RenderAccel"           "true"[/b]
EndSection
```

Awesome! I must say!

edit: Removed [         Option          "AllowGLXWithComposite" "true" ] because it seems to be unstable on my system.

---

### Post by handy on 2006-02-27
There is an, admittedly slim chance, that a BIOS upgrade may give you access to the powernow facility.

BUT, if powernowd is not running, then your CPU should be running flat out all the time!

So, no advantage! :cry:

---

