---
title: "Desktop Effects prevents gnome-terminal from stretching across dual monitors"
date: 2009-11-13
forum: Desktop Environments
---

### Post by caligari2k on 2009-11-13
Greetings All,

I just installed Karmic (9.10) after my hard drive blew up.  I upgraded from 9.04 (restored my files from backup) and got my dual monitors working again.  I'm actually getting really good at this.

My problem is whenever I tried to stretch a gnome-terminal window (or any other window for that matter) across both monitors (start on the left screen and stretch across to the right screen), the edge of the terminal window (or other window) would stop at the edge of the monitor screen.  

I'm running nvidia graphics on a Lenovo T61p.  I've played around with the xorg.conf to no avail.

It took me a while to figure out, but by eventually disabling Desktop Effects (initially, nothing was selected which I found odd), I can now stretch gnome-terminal as well as other windows across both monitors.

Just for the record, I did attempt to move the gnome-terminal window so it took up space on both monitors and then stretch it.  All that did was shrink the window back down to a single monitor.

I did not have this problem on 9.04.

thoughts?  requests for information?

---

### Post by caligari2k on 2009-11-13
One more thing.  Once I have the Desktop Effects set to none, and then I stretch a gnome-terminal window to 2560xwhatever, and then go to enable normal effects, my gnome-terminal window gets resized back down to the default size.  

Quite irritating!  Please tell me this is not a feature!!!

---

### Post by caligari2k on 2009-11-13
I've been able to set up the compiz setting "Resize Window" to "Initiate Windows Resize" to ALT-F8 and it will let me stretch a window across monitors.  However, If I just grab the edge, after stretching across the monitors, it will shrink the window back down to a single monitor.

This has got to be a bug?!

---

### Post by jesper_wilhelmsson on 2009-11-25
I see this bug as well, and I agree, It has got to be a bug! .. or a config issue.. As long as it's not a feature I'm happy. I do not want it this way!
I did not have this problem in 9.04, using the same desktop effects as I am now.

This bug prevents me from working optimally. I have two widescreen displays turned 90 degrees, which is awsome when coding etc. When doing a diff between two source files, previously I had the diff window streched over both screens, giving me one source file on each screen. Now I get the two files jammed into one screen which makes it really hard to do proper diffs since I can't see the whole line at once.

Does anyone have any insight here?

---

### Post by Kewix on 2009-12-04
> **jesper_wilhelmsson said:**
> I see this bug as well, and I agree, It has got to be a bug! .. or a config issue.. As long as it's not a feature I'm happy. I do not want it this way!
I did not have this problem in 9.04, using the same desktop effects as I am now.

This bug prevents me from working optimally. I have two widescreen displays turned 90 degrees, which is awsome when coding etc. When doing a diff between two source files, previously I had the diff window streched over both screens, giving me one source file on each screen. Now I get the two files jammed into one screen which makes it really hard to do proper diffs since I can't see the whole line at once.

Does anyone have any insight here?

Hello Jesper!
I so agree with you! I also use two screens at 90° and it's so wonderful to use meld with two screens that I'm wondering if there is a solution... else I'll maybe switch back to 9.04 but it's so dumb... 

Anyone can help us ?!

---

### Post by ksenter on 2010-01-14
Did you find anything out?  I have the same problem.  I need to have a window span two monitors but when I try to drag it larger than one it snaps back to just one monitor.  Really annoying...

---

### Post by fraenki on 2010-01-15
I have filed a bug report:
[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/507837](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/507837)

Maybe you could add your experiences to this bug report so that it gets some attention.
Please, only useful and precise information.

---

