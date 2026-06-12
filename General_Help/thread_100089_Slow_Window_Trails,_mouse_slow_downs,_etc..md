---
title: "Slow Window Trails, mouse slow downs, etc."
date: 2005-12-06
forum: General Help
---

### Post by starfleetcaptainrob on 2005-12-06
I'm still quite the Ubuntu noob so please be patient!  I'm learning as fast as I can and have overall enjoyed using Ubuntu.  However, I have a rather annoying issue that I have seen addressed on these forums before, but no real answer has been given.  I have been experiencing sort of a slow down when I open new programs, resize windows, drag windows, minimize or maximize windows, etc.  Any sort of OS based animation really.  Also this seems to happen as I get more windows open or tabs on Firefox going.  Things start to slow down when I do any of those actions, for example my mouse gets a little jerky, the window will leave trails as it moves across the screen, etc.  I have been keeping an eye on my CPU usage the few days and have noticed that when these things happen it spikes up to 100%.  I've been trying to figure it out for around two weeks now and have not figured out how to fix it.  I'm not afflicted with it as bad as some other people have been it seems, however it's still rather annoying.  I'm just wondering if anyone else has experienced this and has figured out how to fix it?  I have installed my video card's driver's, I believe I have the right kernel (k-7), so I don't know.

Here are my system specs if that helps at all:

AMD Athlon XP 1150 MHZ
nVidia GeForce FX 5500 256 MB DDR PCI
300 GB Western Digital (Partitioned down to about 160 GB for Ubuntu, 130 GB for Win XP)
1.5 MB of DDR Ram
If there's anything else you need to know let me know...

One other thing I just thought of as I was reading through this again, I have my swap partition only set to about 570 MB and I thought I read somewhere that it should be more.  Would that help at all?  If so, how do I increase it without fubaring everything?  

Thanks!

---

### Post by starfleetcaptainrob on 2005-12-11
Anyone have any ideas?

---

### Post by Lux Perpetua on 2005-12-12
Hi. Does this happen all the time or only when Firefox is up? Because when you drag a window across another window, the second window has to redraw its contents, which can look like dragging if it can't draw fast enough. There might not be anything wrong with your system in this case; it could just be some application (like Firefox) that isn't as efficient as it could be.

---

### Post by veelivar on 2005-12-12
If he has a simlar problem to what I described as "tearing" then it's all the time, not just when dragging over firefox (although that is particually bad).

I know in my case that it is really annoying :(

Dan.

---

### Post by seraphim on 2005-12-12
maybe it's metacity.
metacity is the default windowmanager in ubuntu/gnome.
there are at least two possibilities to replace it:

[http://ubuntuforums.org/showthread.php?t=54476&highlight=metacity](http://ubuntuforums.org/showthread.php?t=54476&highlight=metacity)
this option removes metacity and replaces it by enlightenment.

[http://ubuntuforums.org/showthread.php?t=75527&highlight=metacity](http://ubuntuforums.org/showthread.php?t=75527&highlight=metacity)
here you use xcompmgr to draw the windows. metacity still does some other work

i'm using the second way, it's quite stable already...

---

