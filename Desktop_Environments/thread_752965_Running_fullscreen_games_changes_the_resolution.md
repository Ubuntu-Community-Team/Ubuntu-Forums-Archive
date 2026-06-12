---
title: "Running fullscreen games changes the resolution"
date: 2008-04-12
forum: Desktop Environments
---

### Post by cometa2k7 on 2008-04-12
When I run a fullscreen game like Wolfenstein Enemy Territoy, it all works fine.

However, when I exit the game, the resolution of GNOME changes to 1024x768, it's usually set to 1152x864.

It doesn't seem to matter what resolution the game is set to, it still changes my desktop resolution, and more annoyingly, moves all of the applets and launchers around on the panel

If I run the game, exit, change my resolution back, then run again, it seems to keep 1152x864 as my desktop resolution. But this doesn't really help the problem.

Anyone got a solution?

I have tried using 1024x768 as a resolution, but everything is a bt big, and 1152x864 just works better for me.

---

### Post by cometa2k7 on 2008-04-12
Well, I unlocked all the icons from their places, now they go back to where they were before when I change the resolution back.

The resolution still changes to 1024x768, which is a bit annoying. Any code I can use to change the resolution back to 1152x864?

---

### Post by cometa2k7 on 2008-04-14
Ok, running anything changes fullscreen changes the screen resolution, regardless of the resolution of the fullscreen app. (ie. a game at 1152x864, still changes the resolution back to 1024x768)

About the only thing that doesn't change the resolution is GIMP.

Anyone got any ideas, or at least a script to change it back easily?

---

### Post by warp99 on 2008-04-14
Do you have the resolution '1152x864' plus a modeline for the same in your /etc/X11/xorg.conf file?

---

### Post by cometa2k7 on 2008-04-15
> **warp99 said:**
> Do you have the resolution '1152x864' plus a modeline for the same in your /etc/X11/xorg.conf file?

OK, I looked, and I think I have found the bit that you mentioned, and it does say 1152x864, and Ubuntu lets me set the resolution as this, and use it.

The only problems occur when I run a fullscreen app, like a game or a virtual machine, and most other things.

I quoted the part of the code below, is there anything missing, or wrong? It looks ok to me, but what do you think?

> Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Controller"
	Monitor		"DELL E772p"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection


---

### Post by cometa2k7 on 2008-04-15
Is there ascript that I can run on start up to set the resolution?

Setting the resolution to 1152x864, even though that's what it is already, seems to prevent the problem.

---

### Post by warp99 on 2008-04-15
> **cometa2k7 said:**
> OK, I looked, and I think I have found the bit that you mentioned, and it does say 1152x864, and Ubuntu lets me set the resolution as this, and use it.

The only problems occur when I run a fullscreen app, like a game or a virtual machine, and most other things.

I quoted the part of the code below, is there anything missing, or wrong? It looks ok to me, but what do you think?

That looks good, but it could be that your monitor doesn't return a value for '1152x864' because it may be a non-standard resolution for that monitor so xserver resets it for '1024x768'. If you add a modeline to your monitor section and remove all of the other resolutions that may do the trick. Here's how you would do this:

Open a terminal and get the correct modeline for your monitor:
```
cvt 1152 864
```
output should look like something like this:
```
cvt 1152 864
# 1152x864 59.96 Hz (CVT 1.00M3) hsync: 53.78 kHz; pclk: 81.75 MHz
Modeline "1152x864_60.00"   81.75  1152 1216 1336 1520  864 867 871 897 -hsync +vsync

```
then you would add the modeline to your monitor section of xorg.conf:
```
Section "Monitor"
        Identifier   "DELL E772p"
        HorizSync    30.0 - 70.0
        VertRefresh  50.0 - 160.0
[b]      Modeline "1152x864_60.00"   81.75  1152 1216 1336 1520  864 867 871 897 -hsync +vsync
      Gamma 1.0[/b]
EndSection

```
and to your screen section:
```
Section "Screen"
                    Identifier "Default Screen"
                    Device "Intel Corporation 82865G Integrated Graphics Controller"
                    Monitor "DELL E772p"
                    DefaultDepth 24
                          SubSection "Display"
                    **      Modes "1152x864_60.00"**
                    EndSubSection
EndSection
```

Backup you xorg.conf before you try this at home. You can also add a virtual resolution line to see if that helps:
```
Section "Screen"
                    Identifier "Default Screen"
                    Device "Intel Corporation 82865G Integrated Graphics Controller"
                    Monitor "DELL E772p"
                    DefaultDepth 24
                          SubSection "Display"
                    [b]          Virtual     1152 864
                              Modes      "1152x864_60.00"[/b]
                    EndSubSection
EndSection
```

All of the changes are in **bold**. When you obtain the modeline with the 'cvt' command you can use a different refresh rate if you like. Type 'cvt --help' for more options.

---

### Post by cometa2k7 on 2008-04-15
I tried your suggestion, but it still didn't work. I even tried the one you suggested against.

In fact, it seemed to have no effect at all.

Any other suggestions?

For the time being, I'll just use a seperate account, but I'd prefer to get it fixed, and not have to work around it. Also, others seem to have had similar problems. [http://ubuntuforums.org/showthread.php?t=755091](http://ubuntuforums.org/showthread.php?t=755091)

---

### Post by cometa2k7 on 2008-04-29
This appears to have been fixed in Hardy.

---

