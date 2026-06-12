---
title: "Can't get blender nor any app that uses opengl ..."
date: 2009-03-13
forum: Desktop Environments
---

### Post by hockey97 on 2009-03-13
I can't get blender nor any app that uses opengl to run to work.

I am using the latest version of ubuntu.

I with previous ubuntu's I was able to use blender and opengl with no problem.

the problem occured when I upgrated to the newest version of ubuntu but it was ok on the first installation until my hard drive got wiped out from windowx xp cause windows found a linux hard drive formatted and decided to format the hard drive.

So then I had to re-install linux and windows xp cause I was not able to boot into windows cause of using grub to be the boot loader cause I had a dual os system.

so when I install another copy again on the system this time I got problems with blender and opengl apps.


on top of this I also have problems with youtube videos. They get a very slow frame rate and also  the size of the video shrinks at times and I would get like a glotchy glitchy video. 

Some times when I refresh or type in a new website to get out of youtube videos.

I would still hear the audio playing while I am on other sites and no youtube webpage is one at all meaning it didn't cancle the audio of the youtube video so I would hear it until it finishes this at times causes my system to freeze up.


any ideas of how I can fix the blender/opengl problem and also the youtube problem?

yes I tried to install the other packages not just tried using the none-free flash one.

I tried the others and I got the same results.




here is what blender is shooting out in errors when I try to run it in terminal:

```
guessing 'blender-bin' == '/usr/bin/blender-bin'
Compiled with Python version 2.5.2.
Checking for installed Python... got it!
Xlib:  extension "GLX" missing on display ":0.0".
intern/ghost/intern/GHOST_WindowX11.cpp:105: X11 glxChooseVisual() failed for OpenGL, verify working openGL system!
ERROR: Unable to open Blender window

```

this is what I get.

do you think it can't find blender-bin? hmmm?:(

---

### Post by taurus on 2009-03-13
Sounds to me like both problems have to do with your graphic card.  Which graphic card do you have and have you installed a driver for it, System -> Administration -> Hardware Drivers?

---

