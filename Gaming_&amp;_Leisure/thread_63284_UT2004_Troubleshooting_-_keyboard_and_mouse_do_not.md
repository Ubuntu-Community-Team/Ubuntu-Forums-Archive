---
title: "UT2004 Troubleshooting - keyboard and mouse do not respond"
date: 2005-09-07
forum: Gaming &amp; Leisure
---

### Post by gregory144 on 2005-09-07
I have a recently-new install of Ubuntu 5.04. I have a Radeon 9800 Pro and the fglrx drivers installed correctly. I get ~3100 fps on glxgears. 

Ut2004 loads up nicely and allows me to pick whatever gametype I want and start a game like it normally would. However, during the initial screen (with the guy coming out of the Nvidia logo with the minigun) I cannot press escape to go right to the main menu like normal. Also (this is the main thing), after a level loads normally, I cannot start the game or move around normally. It seems like the mouse and keyboard are not responding to any input. However, I can open the console with ~ and type in commands. The only way to quit the game after that is to use the "exit" or "quit" command from the console. 

I have looked all over the internet for someone with similar problems and cannot find anything like this.

---

### Post by twigsby on 2005-09-07
Go to /home/yourname/.ut2004/System and delete the ut2004.ini and user.ini, restart UT and things should be fixed.

If it doesn't work go to /usr/local/games/ut2004/System and copy the defuser.ini and Default.ini to your .ut2004 in home, then rename them to user and ut2004 respectively.

The first solution always works for me.

---

### Post by gregory144 on 2005-09-07
First solution works for me too! Thanks!

---

### Post by evilghost on 2005-09-07
Your glxgears scores are pretty bad, even with a 9800 PRO.  Did you install the newest fglrx drivers from ATI's website?

Here's a snippet of my xorg.conf file when running a 9800 PRO:

```

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
        #Driver         "ati"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        Option          "NoDCC"
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
        Option          "UseInternalAGPGART" "no"
        VideoRam        131072
EndSection

```

I was seeing around 4000 to 5000 FPS on glxgears, and I know it's a bad score.

---

