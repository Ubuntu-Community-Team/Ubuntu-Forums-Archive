---
title: "America's Army 2.5 will not load...."
date: 2007-04-03
forum: Gaming &amp; Leisure
---

### Post by SniperKIng on 2007-04-03
Hi all

Im having problems with the linux version of america's army 2.5 game and wondering if anyone here could be of help.

The problem is when i start the game its load the splash screen and then just stops and goes off. i have copied and pasted the terminal message below..


[COLOR="Red"]ian@ian-desktop:~$ /home/ian/armyops/armyops
Cheat protection disabled
WARNING: ALC_EXT_capture is subject to change!
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
Either GL_EXT_bgra or glDrawRangeElements not supported- bailing out.

History: 

Exiting due to error[/COLOR]

As i am very new to linux i dont really know what any of this means.If anyone can help me out then i will be very greatfull.

---

### Post by SniperKIng on 2007-04-03
O well thanks for all the help guys...NOT 

I fixed it myself im sick of noone answering my posts

---

### Post by medicineman24 on 2007-05-05
I am having the same problem with the splash screen although im not sure about the error message.  Why won't it run? Uggghh

---

### Post by DoktorSeven on 2007-05-05
First off, the Linux AA client is old and no longer supported, so it might not work at all.  Probably best bet is to try to get the Windows client running through Wine.

Also, for your specific question, do you have your 3d graphics drivers installed?  Type **glxinfo | grep direct** into a console; if you get **direct rendering: No** you'll have to enable 3d graphics drivers.  Check [https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video) for information on how to do so.

If it is enabled, and you have no other problems running 3d games, the old client may be having issues; again, it's no longer supported, and you should try the Windows one.

---

### Post by medicineman24 on 2007-05-05
Thanks DoktorSeven.  Now I know it has to do with my drivers because 3d graphics are not supported (direct rendering or whatever).  I'll couldn't find help in your link (Video documentation) so I'll look around for similar issues.  BTW I'm running on a ATI RADEON 9550 AGP, Ubuntu 7.04.  ATI is kinda tricky with linux.

---

