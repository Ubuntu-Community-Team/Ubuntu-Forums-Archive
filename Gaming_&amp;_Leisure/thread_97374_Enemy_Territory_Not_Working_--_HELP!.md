---
title: "Enemy Territory Not Working -- HELP!"
date: 2005-11-30
forum: Gaming &amp; Leisure
---

### Post by lysis on 2005-11-30
i installed the fglrx as the HOW TO Install Enemy Territory specified, installed enemy territory, and i'm getting a MESA driver errror
```

Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Received signal 11, exiting...

```



i can't figure out how to fix it. anybody care to help?  i went through the wiki and even did the troubleshooting (turn off gnome and do it in console only)

any help would be GREATLY APPRECIATED!!

thanks guys!

---

### Post by shaggydoo on 2005-11-30
I also had that problem, exact same one. Try running it with ```
et "+set r_allowSoftwareGL 1"
``` Unfortunately for me, it was VERY slow. It took about a minute just to load into the menu, and moving the mouse takes about 2 seconds. Still trying to figure that out.

---

### Post by ltmon on 2005-11-30
With both of you what is happening is that ET can't find any hardware based OpenGL accellerators (i.e. your video card).  In that case it falls back on software rendering (Mesa) which works, but because it is not using dedicated graphics hardware is sllllloooooowwww for anything but the most basic graphics.

What type of video cards do you have?

If you have a nvidia make sure you have followed [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

If you have an ATI make sure you have followed [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

For other graphics cards you may be out of luck.  Not many card makers make accellerated drivers for Linux.

L.

---

### Post by lysis on 2005-12-01
like i said above; i followed the directions in ubuntu's wiki for the ATI howto.  and my 9550 card is listed in my sig. =)    

i HAD et working before with my computer system; but something bad happened to the drive and i unfortunately had to format. i lost all of the work i did to ubuntu . . . i'm slowly getting everything working again, but et is the one thing i so far cannot. 

fglrx is what i installe for ati.  i can't get et to recognize this though.  would a re-install of ET fix this, or does it dynamically look for hardware on it's own?

---

### Post by lysis on 2005-12-01
tried the +set_software and it was crap.  BIG crap.  my system WAS working fine with opengl stuff before; but now after i followed the wiki, not even my screensavers that are opengl work right (2.5fps) 

so whatever i did through following the explicit breezy instructions in the wiki made my system worse.

---

### Post by lysis on 2005-12-03
GOOD NEWS

i DID get enemy territory to LOAD. I am unable to get into any of the servers i regularly play in. it says i am banned. i am NOT banned; this problem happens in windows so i simply disable punkbuster, exit, restart, enable punkbuster and join and it works. i'm having the problem where disabling punkbuster isn't saving. i'll click the disable punkbuster button in the server list and it says reboot for it to take effect, i do so, and it's on already.

any suggestions so i can get this running?

---

### Post by yetanothersteve on 2005-12-03
You may want to try updating your punkbuster client manually.

I installed ET into the home folder of my normal user, so I just did this:

```
cd /home/me/enemy-territory/pb
chmod +x pbweb.x86
./pbweb.x86
```

---

