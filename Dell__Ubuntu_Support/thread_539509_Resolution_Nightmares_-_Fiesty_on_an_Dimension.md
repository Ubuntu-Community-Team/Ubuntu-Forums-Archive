---
title: "Resolution Nightmares - Fiesty on an Dimension"
date: 2007-08-31
forum: Dell  Ubuntu Support
---

### Post by Marty McFly on 2007-08-31
I have a dell dimension 2350 and I'm using the onboard video card. My monitor is a Compaq CV715 19" CRT monitor.

I don't know if the problem is my monitor or the video, but ever since I installed 7.0.4 half the time I boot up my screen is distorted and cut off at the top.  Not only that but I can't set a resolution higher than 1024x768.  I made a previous thread about it [here](http://ubuntuforums.org/showthread.php?t=520250) that seems like it made it worse because now it ALWAYS boots distorted.

I really like this operating system but I can't use it if it never views right.  

Any ideas what I can do to troubleshoot this?

---

### Post by marx2k on 2007-08-31
I have read through your thread and from what I understand, Intel video cards/onboard video is usually problematic in general.  It doesn't sound like your video card may be at fault though, since if you CAN bring up gnome, it seems to be running it fine.  However, your monitor may be the issue.. possibly.

Have you considered making custom modelines for xorg.conf? 

Here's some info about modelines:
[http://en.wikipedia.org/wiki/XFree86_Modeline](http://en.wikipedia.org/wiki/XFree86_Modeline)
[http://www.xfree86.org/current/chips4.html](http://www.xfree86.org/current/chips4.html)
[http://www.knowplace.org/pages/howtos/xfree86_modelines_conversion_guide.php](http://www.knowplace.org/pages/howtos/xfree86_modelines_conversion_guide.php)

Heres a few modeline calculator sites: (find out about your monitor's specs before doing this)
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl) (Thats the one I use)
[http://www.tkk.fi/Misc/Electronics/faq/vga2rgb/calc.html](http://www.tkk.fi/Misc/Electronics/faq/vga2rgb/calc.html)
[http://koala.ilog.fr/cgi-bin/nph-colas-modelines](http://koala.ilog.fr/cgi-bin/nph-colas-modelines)

I was having serious issues with overscanning and general resolution naughtiness on my HDTV when outputting from my nVidia video card.  Then I calculated the correct custom modeline for the TV, entered that into xorg.conf, rebooted and all was fine.  Sounds like you may benefit from this.

Hope it helps.

---

