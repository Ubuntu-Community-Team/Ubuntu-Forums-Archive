---
title: "[SOLVED] Nvidia glx-new settings and Compiz"
date: 2007-12-26
forum: Desktop Environments
---

### Post by Princegiri on 2007-12-26
this question has been dealt with only a million times in this forum but I JUST CANT SOLVE THE PROBLEM........
this is my problem........ [bear with me ... still shedding my noobiness]

i noticed the jagged edges on my Compiz Cube ; so that made me yearn for some AntiAliasing.
[I][B]
Background:[/B][/I] I have a Feisty Fawn 32 bit with the 8600 GS harware. I have installed Nvidia drivers through ENVY and it looks like it has installed the Nvidia-glx-new drivers .... this i found by hitting "nvidia" in SM. Also '$glxinfo' returns 'direct rendering: yes'

**PROBLEM**
i looked to Applications>System Tools>Nvidia Settings and out came the panel...

Under Anti Aliasing in the settings window
i did "override application" and set it to 4x...... 
when i quit the window, nothing happens. everything is as it is. {both with compiz cube and my desktop.... isnt the screen supposed to flicker?}

I tried doing the same thing from terminal using ```
$nvidia-settings
``` and ```
$nvidia-settings -l
```
NOTHING........ 
I even followed this thread 
[http://ubuntuforums.org/showthread.php?t=580215&highlight=anti+aliasing+compiz](http://ubuntuforums.org/showthread.php?t=580215&highlight=anti+aliasing+compiz)
and added 'nvidia-settings -l' to the **gnome.desktop** file and the **compiz** script file in /usr/bin

no results even after restarting...... thanks to everyone in advance. loving ubuntu.

---

### Post by Princegiri on 2007-12-26
Bump***

---

### Post by Princegiri on 2007-12-27
BUMp *** pleeeeeeeeeeeeeeeeeese.... im trying really.... 
just end up back on square one everytime,....

---

### Post by Princegiri on 2007-12-27
[SOLVED] Okay somehow my noob instincts took me along the right path...
the force was with me......
i tried a couple of things.... finally i saw in the below thread
[http://ubuntuforums.org/showthread.php?t=540234&highlight=envy+anti+aliasing]("envy+anti+aliasing")
about how invoking the nvidia-settings from sudo made a difference .......

i went all out SUDO and did these things
```
sudo nvidia-settings 
```
changed everything to suit my needs -ticked 'sync to VBLANK', antialiasing at 8x and so on

then went on to add ```
nvidia-settings --load-config-only
``` to the file xinitrc, which is in the directory /etc/X11/xinit/ 

and then a restart fixed it.... no more garish jagged edges on my cube...... 
still though, ```
$sudo nvidia-settings -l
``` and ```
$sudo nvidia-settings --load-config-only
``` have no efffect at all when im sitting in a session.... nothing happens to the monitor (i expect to see some flickering while the card adjusts to new settings or something) AND there is no visible change...... I NEED TO RESTART FOR THINGS TO HAPPEN.... why? i know this thread is already dead.... but took the pain just in case some noob like me needs help....

---

### Post by Cresho on 2007-12-27
well, what you are really asking for is why you cannot change antialiasing configuration or anisotropic filter values while the 3D accelerator is engaged.  YOU CAN'T!  It's like trying to the settings on a video game while the game is running.  what you need to do is shut down compiz and after the change re initialize it.  Nvidia drivers (even in xp and vista) are not designed for 3d environment modification.  It was set up for 2d desktops or you would actually see a change after you hit apply but apply applies if no 3d application is running or nvidia settings would be smart enough to shut it down and re initialize it.

WE ARE USING BLEEDING EDGE STUFF! and like bleeding edge stuff, you start using your brain unlike vista users.

sooo.......

you create 2 empty files on your desktop(right click on screen and.
 "create document and empty file".
one says shutdown_compiz.sh and other says powerup_compiz.sh (if you looked at my last post about antiliasing, you can see a script I wrote for this purpouse for my video game typhoon powerups or shuts down.  It disables and enables compiz)  Now on each file, do this.  right click and under properties->permmisions tick option execute allow file as program.  do the same for the second file you created so both are now executable.

 in  shutdown_compiz.sh, add this following code. (edit with the text editor program and save it.  right click and edit with text editor and save)

#!/bin/bash
killall compiz.real &
metacity --replace &




and in powerup_compiz.sh add this following code. (edit with the text editor program and save it.  right click and edit with text editor and save)

#!/bin/bash
compiz --replace &

so from now on, before modifying nvidia, shutdown compiz and then modify and then power up compiz. :guitar:  when a pop up pops up and displays with questions, click on run.

you can have those two ugly files hanging around in a folder or something but why go there right?  what I did was integrate these executables to my ubuntu desktop.  I added them to my start menu and this is how.

open up your documents. aka file browser. go to view tab and click on "view hiddin files."  now navigate to your desktop where you created the executables and add a period infront of these files.  THEY NOW BECOME INVISIBLE.  put these two files into your home directory under your username.  This is where they will stay.

now open up main menu under preferences so you can add 2 entries.

highlight system tools and add 2 entries.  compiz off direct it to the shutdown compiz sh in your user directory.  If you cannot see invisible files in your location with the choosing application, just right click anywhere in the navigation window and click on view invisible files.do the same with compiz on and navigate that to powerup compiz sh.  now you have those in your start menus under system tools. :popcorn:

---

