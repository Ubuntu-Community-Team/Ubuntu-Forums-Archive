---
title: "Gnome clock applet"
date: 2007-07-05
forum: Desktop Effects &amp; Customization
---

### Post by sra136 on 2007-07-05
How can you, if it is possible, change the theme of the gnome clock applet?  Are there themes for the clock?  Can it be made to look like KDE's clock?

---

### Post by ldrn on 2007-07-10
I'm a recent quasi-convert from KDE (I decided to try gnome again, and the deskbar applet makes me loath to go back) and wanted the gnome clock to do that, too. Unfortunately, I wasn't able to find a way -- if someone else has, I'd appreciate knowing it! 

I did find a neat work around, though it does cater to my tastes; I liked the KDE clock with a dark background and a light font.  You can try this with other dedicated clock programs, too.  It really is a pity, but I couldn't get it to use KDE's actual clock in gnome via appletproxy -- every time I tried, appletproxy complained about needing a "Kickersettings::instance". (This does work fine with other KDE applets, if you were missing any of them in gnome.  I wish KDE had a way to run gnome applets like that -- or is this a kde feature that gnome can do it?)

You need to type this or install gnome-swallow-applet (apt-get install gnome-swallow-applet); then you need to restart Gnome.  The swallower applet does what it sounds like -- it takes other programs and embeds them into the panel.  The area just to the right is where you can click to move or configure the applet; everything else is passed on to the program it captured. 

You can use any clock you wanted. I tried dclock for a time (it's in the repositories, so you can get it with apt) with these settings: dclock -geometry 75x28 -seconds -noblink -bg black -fg cyan -led_off black  -slope 10

It was blurry, though; I found a program that was much nicer, but had to be compiled: [http://www.ibiblio.org/pub/Linux/X11/clocks/ofclock-1.0.tar.gz](http://www.ibiblio.org/pub/Linux/X11/clocks/ofclock-1.0.tar.gz)  It doesn't set its title correctly for the swallower to grab it by default, but you can use "ofclock --title ofclock"  and it works great.  I attached a compiled version in case anyone wanted to use it but didn't have make.

---

