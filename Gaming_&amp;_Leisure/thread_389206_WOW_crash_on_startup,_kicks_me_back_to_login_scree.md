---
title: "WOW crash on startup, kicks me back to login screen"
date: 2007-03-20
forum: Gaming &amp; Leisure
---

### Post by imageburn on 2007-03-20
I've installed wow twice now, first using wine and the latest guide available here, the second time with crossover. Both put their own desktop icon, so I know I'm not starting the same install ( I guess. . .); after trying to start the program it tells me that new hardware has been detected, should i revert to default yes/no, and with either choice kicks me back to login. Havn't seen my wow account in two weeks and time is burning. . . any ideas?

---

### Post by lou1998 on 2007-03-20
Which version of Ubuntu and which version of wine are you using?
What are the hardware specs for your computer?
Did you edit the config.wtf in your WOW directory to make sure you run in opengl mode?

---

### Post by imageburn on 2007-03-20
Ubuntu 6.10, wine 9.35. .  .

---

### Post by imageburn on 2007-03-20
Oh yeah, I forgot those other two. 512mb ram, sempron 3500, geforce 6500 integrated. I know its not bleeding edge, but I should at least get a splash screen even w/o OpenGL. I'm pretty sure I edited the config though, and as of this post I just did a fresh install. Willing to start from a blank slate. I'm also willing to move to cedega if it REALLY helps.

---

### Post by imageburn on 2007-03-20
I've also seen more than one config edit howto in here, and I'm wondering which is most up to date.

---

### Post by hikaricore on 2007-03-20
[https://help.ubuntu.com/community/WorldofWarcraft]("http://help.ubuntu.com/community/WorldofWarcraft#head-1e7bcc69fd00dfcff966213d36ba145e31296771")

Is usually the best guide to follow.

If you CAN start the game in d3d mode, I suggest doing so and setting all of your graphic options to low + turning off full screen glow effects.  This will give you the best chance of the game actually starting.

If you can't start in any mode, add this to your config.wtf:

> SET ffxGlow = "0"

This will disable full screen glow effects, and may fix the problem.

After this launch in opengl see if it runs.

Which version of the nvidia drivers are you using?

If you havn't done so, I suggest installing the latest binary from nividia.com's linux driver section: [http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html)

If you're not comfortable installing the drivers by yourself, you can find an easy installl script here:  [Envy]("http://www.albertomilone.com/nvidia_scripts1.html")

If you've already installed the drivers, make sure you recheck:

```
glxinfo | grep rendering
```

To make sure it returns: direct rendering: **Yes**

You'll probably even need to double check your xorg.conf file to make sure it's running in 24 bit colour.

```
cat /etc/X11/xorg.conf | grep DefaultDepth
```

In my experience I've seen issues running WoW in 16bit colour, but this isn't always the case.  anyway it can't hurt to check.

On the topic of cedega, I'm doubting you'll have any better luck if you can even get the game to launch with wine, as they are essentially the same damn thing.

---

### Post by hikaricore on 2007-03-20
Also there is no wine 9.35.

Below is the return of my wine version check:

> 
[hikaricore@devistate:~ (20.9 Mb)]$ **wine --version**
_wine-0.9.33_


As you can see the command: **wine --version**
Will return your installed version of wine.

The most recent version of wine is always availible at: [http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/)

---

### Post by imageburn on 2007-03-20
Yeah, you're right-on about the version Hikari. Got a coupla' questions about the driver set up tho': 

1- the nVidia install wizard asks me to leave X before running the script. Quick refresh, how exactly do I do this w/o using a terminal?

2- Here's my result for the existing driver check "glxinfo | grep rendering"


    X Error of failed request:  BadAlloc (insufficient resources for operation)
    Major opcode of failed request:  142 (GLX)
    Minor opcode of failed request:  3 (X_GLXCreateContext)
    Serial number of failed request:  16
    Current serial number in output stream:  17

Gotta admit I don't even know what this means. . . but BAD = BAD.
At least I'm running 24bit color tho'.

>>Punker than Rock<<

---

### Post by imageburn on 2007-03-20
P.S.

The Envy script link and the install guide both seem to be dead links. I appreciate the help fellow beatfiend.

---

### Post by hikaricore on 2007-03-20
Sorry I gave the wrong link for envy, here's the right one:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

For the best results of installing graphic drivers you'll want to goto a text terminal.

Hit: ctrl + alt + f1

Then login as your normal user account.

Run this to start envy (after you've downloaded and installed it ofcourse):

```
sudo envy
```

And follow the instructions on screen. :)

And for your crash, this is mentioned in the ubuntu wow howto, which I also linked wrong:

> #

For users with an Nvidia card who have upgraded to Wine 0.9.30 after installing, you may need to reinstall your drivers if you are crashing with the following error message when running WoW from the console:

Major opcode of failed request: 142 (GLX)
Minor opcode of failed request: 3 (X_GLXCreateContext)
Serial number of failed request: 14
Current serial number in output stream: 15




Installing the drivers with envy as I've mentioned above should resolve your issue.

And here's the correct link to the guide:

[http://help.ubuntu.com/community/WorldofWarcraft#head-1e7bcc69fd00dfcff966213d36ba145e31296771](http://help.ubuntu.com/community/WorldofWarcraft#head-1e7bcc69fd00dfcff966213d36ba145e31296771)

I also suggest rebooting your system after installing the drivers, just to make sure X reloads properly.

If you're at the terminal I suggested you installed from you can restart by simply typing:

```
sudo reboot -t now
```

Good luck,,

--Aaron

p.s. going back in-game to farm :P  i'll check back here after awhile to see if you'd have any luck

---

### Post by Moeru on 2007-03-20
Hikari,

you ever had a problem with the system locking up after hitting Character Panel?

---

### Post by hikaricore on 2007-03-20
> **Moeru said:**
> Hikari,

you ever had a problem with the system locking up after hitting Character Panel?

Can't say I really have, only lockups I ever get are when I try to overclock my PCI GeForce too high.

ROFL

400mhz FSB + GeForce 6200 = FTL

Only suggestion I can give you is launch the game windowed from a terminal and see if you get a specific error when I locks up.  Even if it crashes you'll be able to see the terminal output at that point.  :)

My guess is that your cpu or video card cpu might be overheating, but I can't really give you much more info than that.

---

