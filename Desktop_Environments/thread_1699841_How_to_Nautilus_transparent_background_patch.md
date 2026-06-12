---
title: "How to: Nautilus transparent background patch"
date: 2011-03-04
forum: Desktop Environments
---

### Post by pr3ddi on 2011-03-04
**[Nautilus transparent background patch]("http://forum.compiz.org/viewtopic.php?f=114&t=34249#p108463")**

             [[IMG]http://forum.compiz.org/styles/prosilver/imageset/icon_post_target.gif[/IMG]]("http://forum.compiz.org/viewtopic.php?p=108463#p108463")by **[pr3ddi]("http://forum.compiz.org/memberlist.php?mode=viewprofile&u=28949")** » Wed Mar 02, 2011 11:10 pm 
                            here you go ... a nautilus transparent background patch for everone who is not afraid to compile nautilus from source :-)

**new version available here --- [http://ubuntuforums.org/showthread.php?t=1814132](http://ubuntuforums.org/showthread.php?t=1814132)**

what you will get:
- a transparent nautilus desktop window in compiz, which has the usual desktop integration (icons and context menu)
- a working wallpaper plugin, that can be set to show a different wallpaper on every screen
- you can even use mplayer to play a video on your background

how it's done:
- the nautilus desktop window is modified to render a transpart background, if a composited screen is detected
- window type is changed from _NET_WM_WINDOW_TYPE_DESKTOP to _NET_WM_WINDOW_TYPE_NOTIFICATION
- window is set to be keept below all other windows and the mouse wheel event is proxied to the root window

the patch was developed for nautilus 2.28.1 (Ubuntu 9.10) first and then applied to nautilus 2.30.1 (Ubuntu 10.04)
the only difference in 2.28.1 is that there is one more row (below set_image_properties) in the original eel-background.c

please follow the detailed instructions in the 98_transparent-background.txt file

have a nice day

pr3ddi

---

### Post by fooey on 2011-03-08
cool. got a screenshot of what it'd look like by chance?

---

### Post by pr3ddi on 2011-03-11
it would be difficult to see on a screenshot, but I will try to describe it ...

this patch works on the desktop background, which is being drawn by nautilus
it has no effect on the nautilus windows, which are being used to show folders and files

standard nautilus desktop behaviour
- you can have only one background image for all virtual desktops
- switching virtual desktops does not affect background image (it's fixed and does not move)
- you can't play a video on your background

nautilus desktop with patch
- you can have one background image per virtual desktop
- background images slide in/out together with the windows when switching virtual desktops
- you can play a video on your background

video command, that plays random videos from a folder
xwinwrap -ni -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet -loop 0 -shuffle *.mp4

---

### Post by wahyuaja on 2011-03-12
i don't understand ...

---

### Post by hawthornso23 on 2011-03-12
@Wayjuaja:

Compiz has the ability to do cool stuff with your desktop backgrounds like putting videos on there or having a different wallpaper on each desktop. But you can't see any of this goodness if you are a gnome user because nautilus plasters its own wallpaper over the top and covers it up so you can't see it. 

There is a setting in nautilus to tell it to stop drawing the desktop, but this turns off everything to do with the desktop - no icons - no drag and drop to the desktop - no right click context menu. For most people it isn't worth the loss of functionality.

What the patch does is tell nautilus to use transparent wallpaper, which it normally refuses to do, so you can still have the icons and all that useful nautilus desktop stuff, but you can also see what compiz is doing underneath.

This problem has existed for years and lots of people have complained about it. The gnome developers should have done a fix like this a long time ago, but refused. It is well known that there is friction between the gnome people and the compiz people and many suspect that the refusal is at least in part spitefully motivated. 

However the beauty of open source is that anyone can read and modify the code, as the OP has now done.

---

### Post by Adrastus on 2011-04-21
[FONT=Arial][SIZE=3]First off, thank you very much pr3ddi for sharing this!  This is why I love Linux.

But unfortunately, I can't get it to work.  I'm running 10.10 64-bit and not having any luck.  I found your posts here:[/SIZE][/FONT][FONT=Arial][SIZE=3][URL="http://forum.compiz.org/viewtopic.php?t=34249"]
http://forum.compiz.org/viewtopic.php?t=34249[/URL]

and I replaced GDK_DISPLAY with "gdk_display_get_default()" just using a global find and replace and I commented out patches 82 and 89 (only commented out 89 after I tried it once with out commenting) in the series file but I still get errors when I run make:[/SIZE][/FONT]

```
Making all in libnautilus-private
make[2]: Entering directory `/usr/local/src/nautilus-2.32.0/libnautilus-private'
  CC     nautilus-autorun.lo
gcc: @APP_INDICATOR_CFLAGS@: No such file or directory
make[2]: *** [nautilus-autorun.lo] Error 1
make[2]: Leaving directory `/usr/local/src/nautilus-2.32.0/libnautilus-private'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/nautilus-2.32.0'
make: *** [all] Error 2
```[FONT=Arial][SIZE=3]I've never actually built anything from source before but it looked like fun and Wallpapoz was getting annoyingly slow and I don't like not having icons...so I'm stuck.
[/SIZE][/FONT][FONT=Arial][SIZE=3]
Has anyone figured this out for Nautilus 2.32.0 yet?[/SIZE][/FONT]

---

### Post by miousername on 2011-05-06
Thank you very much! Great job it works very good in ubuntu 10.04 32 bit!

I installed gnome-color-chooser to modify desktop name icon color because they were dark and I couldn't read them.

To solve black background issue with this patch I created a script named delaynautilus with :

#!/bin/sh

sleep 5s && nautilus -q


after I copied it in /usr/local/bin/

and I added a new voice on starup application manager that calls the script and the problem seems to be solved.


Ps. After download the package nautilus with sudo apt-get source nautilus and applied the patch I would suggest to compile the package with:

dpkg-buildpackage -rfakeroot


in this way you can install directly the modified debian package!

thank you very much for your patch!

---

### Post by alex_o on 2011-06-04
11.04?

---

### Post by gs777 on 2011-06-06
give some screenshots

---

### Post by fabriciomarques1 on 2011-10-22
Thanks a lot! It's working very well.

Just one thing:
The "show desktop" buttom makes everything (including icons), except the background, disapear. And, when I click the button again, everything comes back...

Any suggestion?

---

### Post by fabriciomarques1 on 2011-10-24
> **miousername said:**
> Thank you very much! Great job it works very good in ubuntu 10.04 32 bit!

I installed gnome-color-chooser to modify desktop name icon color because they were dark and I couldn't read them.

To solve black background issue with this patch I created a script named delaynautilus with :

#!/bin/sh

sleep 5s && nautilus -q


after I copied it in /usr/local/bin/

and I added a new voice on starup application manager that calls the script and the problem seems to be solved.


Ps. After download the package nautilus with sudo apt-get source nautilus and applied the patch I would suggest to compile the package with:

dpkg-buildpackage -rfakeroot


in this way you can install directly the modified debian package!

thank you very much for your patch!
You said you "added a new voice on starup application manager that calls the script". Could you explain how to do that, please?

I've reproduced the script and copied it in the directory the way you said. Then I went to System>Preferences>Startup Applications and select and mark delaynautilus, but everytime I logout or turn off the computer, I have to run the command nautilus -q manually because nothing happens.

Any help will be welcome. Thanks!

---

