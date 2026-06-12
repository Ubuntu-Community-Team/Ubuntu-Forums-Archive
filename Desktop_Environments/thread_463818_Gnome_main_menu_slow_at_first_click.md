---
title: "Gnome main menu slow at first click"
date: 2007-06-04
forum: Desktop Environments
---

### Post by ingvald.straume on 2007-06-04
I! I'm a secondary school teacher in Norway. I've been doing some job employing Linux at my school. We have about 20 student PCs running ubuntu Linux Edgy Eft. These are Pentium III with 256 MB RAM. I'm a devoted fan of Linux, and I like many of the features of Gnome.

But there's ONE thing about Gnome that I really dislike: When opening the main menu (by clicking it) the first time after logon, or after running killall gnome-panel, it takes several seconds for it to respond. I've found out that this has something to do with gnome reading a large number of .desktop and icon files from the hard-disk.

Gnome shows about the same beahaviour when I double-click a desktop icon (i.e. a folder): It takes too long time before the Nautilus window appears on screen.

Is there some way to make this annoying "feature" disappear? Maybe some sort of icon caching would be great in this case, but I cannot figure out how to make it work? (I'm not much of a hacker myself.)

Can someone please help me.

Ingvald Straume
:(

---

### Post by blackened on 2007-06-04
One thing that might help would be to use the menu editor and replace all svg icons in the menu with raster images (generally the 24x24 pixel pngs of corresponding subdirectory and filename in the parent folder) as pngs of this size would likely take less time to render.

The downside to this is that it would be tremendously time consuming, not to mention tedious.

---

### Post by ingvald.straume on 2007-06-04
Thank you! I'll give that a try.

---

### Post by ingvald.straume on 2007-06-04
I ran the following commands in a terminal window:

killall gnome-panel
touch /tmp/now

Then i clicked the gnome main menu and waited for 2-3 seconds till it emerged.
Finally I ran this command in the terminal window:

find /usr/share -type f -anewer /tmp/now

From the output of the last command, i found that most file accesses triggered by me clicking the gnome main menu were of type .directory. I found one or two .svg files. I renamed the folders containing those svg files. Next time i ran the commands above, no .svg files appeared as part of the output from the last command. I'm sorry to say i could not notice any speed improvements when clicking the gnome main menu first time after logging on (or after restarting the gnome-panel). Thank you for trying to help me anyway.

Ingvald

---

### Post by ramjet_1953 on 2007-06-04
I think that a major issue here is with your hardware.

Pentium III's with 256Mb of RAM is pretty much at the lower limit for GNOME or KDE.

You may want to try one of the more lightweight GUI's like XFCE.

Either that, or add mor RAM to the PC's.

Regards,
Roger :cool:

---

### Post by orb9220 on 2007-06-05
> I think that a major issue here is with your hardware.

Nope this was an issue last year and there was a fix but can't find it.
I have a P4 1.3 with 640mb of ram and have this issue of first click delay of menu's and it a setting or adding something to a thinga ma jig file. "Oh! Brain and Brain, What is Brain!"

I'll keep looking and get back if I find it.

---

### Post by panso on 2007-08-11
I have the same issue. not 2-3 seconds, more like 1-2, but a noticable lag compared to subsequent uses of the main menu. To clarify, the menu bar applet show no lag whatsoever, its only the meny applet. i.e. the ubuntu icon which has preferences and administration under the same menu rather than under seperate task bar menus.

Has anyone come across an answer?

This has always been an issue with ubuntu for me since 2 years ago on a P4 with 512 RAM and now with an Athlon X2 64 with 1G RAM. So I am sure this is not hardware specific. Copmiz-fusion runs like a dream on my system (the problem occurs even without compiz)

Cheers

---

### Post by Tutelar on 2007-09-16
Try turning off "Play system sounds" from the Sounds tab of Sound Preferences (System/Preferences/Sound menu).

Worked for me.

---

### Post by marcrosoft on 2007-09-17
Ingvald, I believe I have the answer to your problem.  You need to cache the icons in the menu.  I notice this delay as well an I have dual core 2gigs of ram with an Nvidia 8800gts so its NOT a hardware issue.

I wrote an article on it: [ Speed up the Gnome Menu and Fix the Annoying Icon Delay]("http://www.marksanborn.net/linux/speed-up-the-gnome-menu-and-fix-the-annoying-icon-delay/")

Btw, I love Norway I was in Aalesund this summer.

Mark

---

### Post by maharbA on 2007-09-30
I have the same problem: the first time I click the Gnome Main Menu it takes a few seconds to load (I think it also does it if I haven't clicked it in a while, but I'm not sure). I do notice the icon lag when opening each sub-menu but I'm not too upset by that -- just the initial few seconds of waiting with no feedback (did i click it? maybe I should click it again -- dang!)

marcrosoft: I followed your guide (the first part, at least -- like I said, sub-menus aren't bothering me) and I'm still getting the delay. Do I have to do it on every login?

like panso said, this only happens with Gnome Main Menu -- not the default "Applications", "Places", "System" menu bar applet.

If it must take so long to open, a little feedback would be nice, like the spinning wheel cursor or just have the applet flash when clicked -- just so I know I've clicked it!

---

### Post by marcrosoft on 2007-10-08
For me the delay seemed to go away; however, I believe you need to update the cache every time a new menu item(icon) is added or changed.

"Do I have to do it on every login?"

For me it worked doing it just once.  You can test what would happen caching on startup by making a bash script with the command in my guide and run it by going into System > Preferences > Sessions and click New.

Hope it helps. :)

---

### Post by Dakkar on 2007-10-15
Hello, is there a way to know what Icon theme I’m using, I looked at the theme manager and my icon theme name is OSX but I don’t see any folder with that name under /usr/share/icons, could be in another location?

Thanks in advance

---

### Post by parmdeep on 2008-02-25
thank you macrosoft, worked like a charm for me,

---

