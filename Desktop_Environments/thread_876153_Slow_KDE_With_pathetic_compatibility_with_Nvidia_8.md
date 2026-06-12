---
title: "Slow KDE With pathetic compatibility with Nvidia 8800 GT and Compiz"
date: 2008-07-31
forum: Desktop Environments
---

### Post by SandyM on 2008-07-31
I am new to ubuntu and was thus using Gnome as my default Environment but the latest buzz about new KDE 4.1 powered by Plasma 3d interface lured me to try KDE but all my initial excitment sunk when I started using it.

I think it is horrible with my Nvidia 8800gt card since it is slow and even mimizing and maximizing lacks smoothness and looks awkward when compared to compiz effects in Gnome.

Even Emerald seem to better the default theme manager in new KDE. And of course I am missing dazzling compiz effects which seems to be incompatible with the KDE 4.1.

Could anybody advise how to use compiz/emerald in KDE 4.1 as I am unimpressed with the inbuilt dekstop effects and how can I do away with its slowness. (like minimizin and maximosing)

---

### Post by chucky chuckaluck on 2008-08-01
someone on the arch forums was having similar problems and i guess there is an issue with kde4 and nvidia. here's a related link - [http://techbase.kde.org/User:Lemma/KDE4-NVIDIA](http://techbase.kde.org/User:Lemma/KDE4-NVIDIA)
not sure that'll be much help.

---

### Post by flying_icarus on 2008-08-01
You can also try changing the default acceleration settings -> Open "Desktop Effects" configuration from somewhere (i.e. right click on a window title and choose "configure window behaviour" or find it in "system settings" applet under "Desktop"). Click on advanced and try changing the options.

For me (also on a 8800GT) the winning combination is the following:
Compositing Type - OpenGL
Keep thumbnails of hidden windows up to date - disabled
OpenGL Modde - shared memory
Texture filter - nearest (fastest)
Direct rendering - enabled
Use VSync - disabled

With the VSync disabling I got the best improvement - cpu usage dropped from ~40-50% to below 1%.

The effects still stutter and skip sometimes, but much less so than before. Apparently the problem is between NVidias OpenGL implementation in the proprietary driver and the way KDE uses OpenGL, hopefully this will be improoved as time goes by.

Good luck! ;)

Oh, and I tried the settings from the link chucky posted - "nvidia-settings -a InitialPixmapPlacement=2" also improoved speed even more.

---

### Post by Growbag on 2008-08-01
KDE 4 is BETA software, but the KDE4 team and certain Distro makers insist on not informing you about that!

It is NOT ready for general use, and has many problems!!!

It has issues with Nvidia drivers that the developers blame on Nvidia.

Although no other desktop has problems with the proprietary Nvidia drivers, so make your own mind up about that!

The 4.1 "release" is great on openSUSE, although it is still a little sluggish with Nvidia cards.

Just remove it and forget you ever heard about it until 4.2!!

---

### Post by flying_icarus on 2008-08-01
Well, I wouldn't use such strong discouraging words... but Growbag is basically right.

I actually watch the evolution of KDE 4.x like an interesting TV series - you have great potential in the characters and the plot, but you're dying to see what happens to them and if they live up to your expectations. Sometimes they don't at first but make it good in the end, sometime main characters die but are replaced by good alternates (look at konqureror as a filemanager & dolphin), and generally you alywas have something to look forward to to keep you entertained and interested. :)

You have a good, stabile and working enviroment you like allready - it's the one you are currently using, Gnome - so you are not abandoned while KDE 4.x is shaping up and you can track it from the sidelines like a hobby. ;)

If you installed KDE 4.1 and find it lacking, take a look arround it and imagine what could maybe be done in the future with the ideas presented and with 4.1 as a starting point, then come back to look at 4.2 and maybe be surprised. ;)

KDE 4.x is an evolving thing, things are moving and improving month by month and release by release. If you don't like it at all, then there is not much to do about it since the basic direction is set, but if there are things you like and you're put off by bugs, performance or lack of features, don't give up on it yet. Just wait a bit untill there is more of the stuff you like then there is of the stuff you don't. :)

---

### Post by nossifer on 2009-01-29
@flying_icarus

thanks.  tried those under kde4.2 and it seems to have definately helped.
i am shocked that this isnt fixed for 4.2.  but... it isnt so it seems.

---

