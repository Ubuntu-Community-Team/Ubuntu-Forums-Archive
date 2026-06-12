---
title: "Slow slideshow screensaver in Oneiric and Precise"
date: 2012-05-15
forum: Desktop Environments
---

### Post by bravo sierra echo on 2012-05-15
This has been logged as a bug but obviously hasn't been fixed yet.  In the meantime, does anyone have a workaround?  Maybe a config file I can edit?

Certain transition effects run ludicrously slowly in the slideshow screensaver on KDE.  It was fine on Natty Narwhal, but the bug came in under Oneiric Ocelot and it's still there on Precise Pangolin.

By slow, I mean 20 minutes to go from one image to the next on my machine, which has twin 3.00GHZ processors, 3GB RAM and a Nvidia GeForce graphics card.  My laptop, which has a lower spec (2GHZ, 2GB) suffers almost exactly the same times so I do believe this is a programming error rather than an issue with system spec.

Like I say, it's been reported a bug so I'm sure it'll get fixed eventually.  In the meantime, the preferences do not allow me to choose which transition effects I use.

Is there a config file I can edit to omit the problem transition effects?  Or turn transition effects off completely?

This might sound like a small issue, but it's not - it might sound daft but I do use the screensaver as a very large digital photoframe!

---

### Post by VanillaMozilla on 2012-05-16
Many of the screensavers are problematic, and that's why they're not even distributed with Ubuntu.  You could try one of the image viewers instead.  They all have a full-screen, slideshow mode.

---

### Post by SeijiSensei on 2012-05-16
For a slideshow, just use Gwenview in full-screen mode.  It's included with Kubuntu by default.  You can control the pace of display by clicking the "wrench" icon in the bar at the top of the screen.

---

### Post by zombifier25 on 2012-05-16
> **VanillaMozilla said:**
> Many of the screensavers are problematic, and that's why they're not even distributed with Ubuntu.  You could try one of the image viewers instead.  They all have a full-screen, slideshow mode.

Mine works fine. The reason no screensavers are distributed with Ubuntu from 11.10 onward is on GNOME's side, not Canonical. Apparently GNOME decided that people are not allowed to have cool-looking desktops while they're gone and removed gnome-screensaver's ability of using screensavers completely.

Back to topic: Maybe your card's NVIDIA driver is responsible for not doing OpenGL properly. I use Noveau (Linux's built-in driver) and experienced no issues. You're better of using an image viewer capable of slideshows (which VanillaMozilla and SeijiSensei suggested nicely above)

---

### Post by VanillaMozilla on 2012-05-16
To be more precise, the gnome-screensaver in Gnome 3 has only a screen blanker.  Quite a few of the screensavers have multiple, unhandled bug reports scattered about the Internet.  I have found that some of the best ones indeed can lock up computers.  Documentation seems to indicate that implementing screensavers in Linux is Way Too Complicated.  It's my *assumption* that the Gnome guys are not just being killjoys (in this case), but that they have no frickin' idea how to make a screensaver that's guaranteed to work.  This could be the first known example of reliability and function taking priority over frivolous fun.

---

### Post by SeijiSensei on 2012-05-17
I installed the array of KDE screensavers via "sudo apt-get install kscreensaver-*". You can access them via System Settings > Display > Screensaver.  I chose the Slide Show entry under Banners and Pictures.  Some of the transitions are slow, but none of them take more than a minute at most, usually quite a bit less.  I have an NVIDIA 9500GT-based graphics adapter; YMMV.

---

### Post by undecidable on 2012-09-20
fwiw just in case bravo sierra echo is still following this:

a.  Agree it is a pain.  On my Preision workstation with a Quadro FX graphics card, some transitions look like they will take an hour.  Also takes a slightly long time to exit hte screensaver.  
b.  Given the black-box nature of nv drivers, hard to see it getting a priority.
c.  But the nouveau driver didn't work for me, so had to go to nv driver. There is no onboard graphics on this machine.
d.  Gwenview etc are not useful here. They do not provide screen locking.
e.  Already have all effects disabled.  
f.  Several years ago (6.06 I thnk) when I first started using Kubuntu, I askled about a config file for the slideshow screensaver - never found one.

---

### Post by undecidable on 2012-09-30
Further to the above, I have now installed 12.04 on 3 machines:
.  a Precision workstation with an NVidia Quadro Fx1400 card, driver vsn 295.49
.  a Thinkpad with an NVidia NVS3100M card, driver vsn 295.49
.  a Thinkpad with Intel graphics.

The problem is the same on both machines with NVidia cards, doesn't happen on the machine with the Intel graphics card.

Personally I have always found the transitions ugly, and would like to turn them off anyway.  But have never found a way.

If anyone knows of a method, I will send serious Good Kharma your way.

---

### Post by undecidable on 2012-10-01
I spoke too soon.  Also happens with the open driver on the intel graphics card.

---

### Post by secayford on 2013-06-14
According to the comment in this bug report ([https://bugs.kde.org/show_bug.cgi?id=182104#c11](https://bugs.kde.org/show_bug.cgi?id=182104#c11)) you can add the line "EffectsEnabled=false" to the Settings section of ~/.kde/share/config/kslideshow.kssrc

This seems to have worked for me.

---

### Post by undecidable on 2013-06-15
Correct indeed.  I had had this problem for so long, and tested so many fixes, I lost sight of a few basics.  
(eg I had set my screensaver image dir to have just one image to stop the transitions).
when I just re-tested, with multiple images and a fixed config file, it works.  

Am not the op, so can't mark this as Solved.

Thanks for that reminder.

---

### Post by bravo sierra echo on 2014-01-04
> **secayford said:**
> According to the comment in this bug report ([https://bugs.kde.org/show_bug.cgi?id=182104#c11](https://bugs.kde.org/show_bug.cgi?id=182104#c11)) you can add the line "EffectsEnabled=false" to the Settings section of ~/.kde/share/config/kslideshow.kssrc

This seems to have worked for me.

This has done it :)

I'd forgotten about posting this thread and have just been putting up with it until now but THANK YOU.

---

