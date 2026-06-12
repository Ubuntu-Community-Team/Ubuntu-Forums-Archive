---
title: "Enemy Territory: Lags and fullscreen"
date: 2005-03-28
forum: Gaming &amp; Leisure
---

### Post by divel on 2005-03-28
Hi everyone! I'm a big fan of ET and have just upgraded to Hoary. I've got some problems with ET however. I was able to circumvent the problem with ET not starting because of the sound issue, so that is sorted out. It seems that I can't get ET working in fullscreen; there is a border (larger or smaller based on my resolution settings in ET) that shows part of the last GL screensaver? Anyone know how to handle this? 

My other problem is that I am not getting the smooth graphics that I used to on windows. I've got a Radeon 9700 128 MB, so I should be okay with the hardware part of it. I realise that this might have something to do with the problem I mentioned with the border showing up. Any suggestions?

Divel

---

### Post by ubuntu-geek on 2005-03-28
In your /etc/X11/xorg.conf do you have "ati" or "fglrx" as the driver? If you have ATI you will want to install the better driver.

sudo apt-get install xorg-driver-fglrx
echo fglrx | sudo tee -a /etc/modules
sudo sed -i -e 's/"ati"/"fglrx"/' /etc/X11/xorg.conf

Reboot that should do it.

More information can be found here: [http://ubuntuforums.org/showthread.php?t=3567](http://ubuntuforums.org/showthread.php?t=3567)

---

### Post by divel on 2005-03-29
[QUOTE=ubuntu-geek]In your /etc/X11/xorg.conf do you have "ati" or "fglrx" as the driver? If you have ATI you will want to install the better driver.

sudo apt-get install xorg-driver-fglrx
echo fglrx | sudo tee -a /etc/modules
sudo sed -i -e 's/"ati"/"fglrx"/' /etc/X11/xorg.conf

Reboot that should do it.

More information can be found here: [http://ubuntuforums.org/showthread.php?t=3567](http://ubuntuforums.org/showthread.php?t=3567)[/QUOTE]

Thanks, but I am using the fglrx-drivers, and when running fgl_glxgears I get 
1381 frames in 5.0 seconds = 276.200 FPS, so I think that this works all right.

---

### Post by psyko-lefse on 2005-03-29
Is the resolution ET uses supported by the xorg.conf? If it isn`t, you have to add it manually.
Btw, how did you fix the sound problem? Do you just kill esd, or have you got a better solution?

---

### Post by telmo on 2005-03-29
[QUOTE=divel]Hi everyone! I'm a big fan of ET and have just upgraded to Hoary. I've got some problems with ET however. I was able to circumvent the problem with ET not starting because of the sound issue, so that is sorted out. It seems that I can't get ET working in fullscreen; there is a border (larger or smaller based on my resolution settings in ET) that shows part of the last GL screensaver? Anyone know how to handle this? 

My other problem is that I am not getting the smooth graphics that I used to on windows. I've got a Radeon 9700 128 MB, so I should be okay with the hardware part of it. I realise that this might have something to do with the problem I mentioned with the border showing up. Any suggestions?

Divel[/QUOTE]

I know exactly what you mean! I have the same problem and it sucks! The fullscreen thing happens to me also in other games such as Counter Strike. I hate it!

Any ideas anyone?

---

### Post by telmo on 2005-04-03
Anyone?

---

### Post by fackamato on 2005-04-03
[QUOTE=divel]Thanks, but I am using the fglrx-drivers, and when running fgl_glxgears I get 
1381 frames in 5.0 seconds = 276.200 FPS, so I think that this works all right.[/QUOTE]

You're kidding right, 276 fps with a 9700? My friend has a 9800 Pro, he gets 4500 fps. You should at LEAST get 3500 fps. Your glx acceleration is not working, please post xorg.conf and xorg log...

---

### Post by divel on 2005-04-08
Sorry about that - 

1392 frames in 5.0 seconds = 278.400 FPS is the correct output.

I've changed my x-org file to support the video-modes I'm using in ET, and that has solved the problem with part of the gl-screensaver showing. 

However I need to use killall -9 esd before using the game.

Thor

---

### Post by maqi on 2005-04-12
I posted a rough and ready script to fix this on [this thread](http://www.ubuntuforums.org/showthread.php?t=22109&highlight=enemy+territory). Just save it somewhere and make it executable. Then put a launcher on the panel which points to the script instead of directly to et.

But there must be a better way ...  [-o< 

maqi

---

### Post by telmo on 2005-04-25
What about fullscreen? If i choose 800x600 or 1024x768 i don't get fullscreen. And i can't choose my native resolution 1280x800! :(

Anyone?

---

### Post by dahtoy on 2005-06-29
You need to have the resolution you wish to play in specified in your xorg.conf file under the display subsection of the screen section. The file can be found at /etc/X11/xorg.conf , for example if you want to be able to play in 1024x768 or 1280x1024:

```

# Example xorg.conf screen setup
Section "Screen"
    Identifier  "Screen0"
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor0"
    DefaultDepth 24

    Subsection "Display"
        Depth       24
        [COLOR=Red]Modes       "1280x1024" "1024x768"[/COLOR]
        ViewPort    0 0
    EndSubsection
EndSection

```

You can only play at resolutions supported by ET so unfortunately no widescreen, i think the resolutions are 640x480, 800x600, 1024x768, 1164x873, 1280x1024. Just make sure your monitor resolutions are right in xorg.conf.

The problem with sound is that most onboard devices dont have hardware mixers. This means that gnome will lock up your soundcard with esd and then any program that tries to access it will crash/fail. The best way to get around this (rather then killing esd everytime you want to use sound outside esd) is specified in Chua Wen Kiat ubuntu starter guide.

[http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly)

---

### Post by factotum218 on 2006-11-03
I read through because I have the same problems. No sound and launches in an unusably slow window. I checked my xorg.conf and have everything from 1600x1200 all the way down to 640x480 in 24 trough 8 bit capible. Still no dice. Im guessing it launches at 800x600 by default. I tried tinkering with the setting in the game menu, but I could barely get the mouse to move enough to be able to quit and exit the game.
Has there been any solution found at all?

---

### Post by gr83 on 2006-12-20
You guys are making Enemy Territory on Linux more complicated than it really is in my opinion.  I got 44KHz audio, and full openGL widescreen working on a LinuxCertified LC2440N without any problems when appending the appropriate cvar commands to the executable. e.g.:

Audio without messing around with ESD: ```
+set snddevice /dev/dsp
```

Widescreen without having any resolution modes in xorg.conf: ```
+set r_fullscreen 1 +set r_mode -1 +set r_customwidth 1680 +set r_customheight 1050
```

I made a shell script in /usr/local/games/enemyterritory called widescreen.  It contains the following:

```
./et +set r_fullscreen 1 +set r_mode -1 +set r_customwidth 1680 +set r_customheight 1050 +set snddevice /dev/dsp +set g_fov 110
```

There's a ton more cvar commands that you can play around with too but it's mostly tweaking the game performance.

Edit: Same procedures apply to any Quake 3 engine based game and likely any other Quake based engine/game with different cvar commands.

---

