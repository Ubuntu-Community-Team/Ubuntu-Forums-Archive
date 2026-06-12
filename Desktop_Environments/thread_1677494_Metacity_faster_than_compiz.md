---
title: "Metacity faster than compiz?"
date: 2011-01-28
forum: Desktop Environments
---

### Post by yuler on 2011-01-28
I recently installed "fusion-icon" to test speeds between Metacity and Compiz on my older nvidia graphics cards (6200, 256mb) video card.  My results are mixed.

When using any program that scrolls the window (e.g. Firefox 3.6.13, Nautilus, PDF Viewer, rhythmbox, etc), I found Metacity is smoother and responds quicker than Compiz.  

However, Compiz is nearly instantaneous switching apps.  With Metacity, the screen redraws in 1/8 to 1/4 seconds.

Metacity is failing to draw underneath popup boxes (e.g. tooltips) when the screen scolls.  I have to scroll the affected area offscreen and back to get it to draw correctly.

Are there any tests, settings, or configurations to get one or the other working entirely?

---

### Post by tgalati4 on 2011-01-28
The open source graphics drivers for both ATI and nVidia are not as polished as their proprietary Windows counterparts.  The proprietary Linux graphics drivers for ATI and nVidia are an improvement in some cases, but you often have to recompile the drivers with each kernel update.

There are lots of switches for both ATI and nVidia cards that you can set in xorg.conf, but I doubt you will see much improvement.  The default values are usually good enough to work and changing them tends to break other things.

Do a search on your specific card and see what comes up for xorg switches.

---

### Post by yuler on 2011-02-07
Lowering the screen res to 1024x768 helped, but I still get sluggishness.  Using "top -d.5" (to get .5 updates), I saw the xorg process is a culprit.  If I scroll on any screen (a log file, Firefox, etc), the CPU spikes as far as 60%!  Granted, this is an computer circa 2004 (1.6Ghz 1GB 333Mhz DRAM), but is that normal?  

I also applied most tweaks from [Linux Fanatic]("http://linuxfanatic.wordpress.com/").  Most notable was changing swappiness from 60 to 10 so the system swaps only 10% of the time.  The swap is still on sda, which is the same hard drive as the OS, so it was slowing down.  I plan on moving the swap to sdb.

I am hunting [http://wiki.x.org](http://wiki.x.org), among other sites for answers.  I am also considering installing xcfe instead of GNOME.

---

### Post by 3Miro on 2011-02-07
Compiz utilizes your GPU, while Metacity relies more on the CPU, hence the difference in performance. Try going into Gconf-editor (that is Alt + F2 and then type gconf-editor), find Apps -> Metacity and look for "composition manager". Try turning it on/off to see if this has any effect on performance.

I had some of those issues on my laptop (Intel video + external monitor). My utimate solution was to use OpenBox in place of Matacity and Compiz (Openbox should be in the Software Center).

---

