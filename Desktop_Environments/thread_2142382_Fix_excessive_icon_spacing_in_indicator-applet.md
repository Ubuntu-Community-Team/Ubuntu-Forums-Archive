---
title: "Fix excessive icon spacing in indicator-applet"
date: 2013-05-05
forum: Desktop Environments
---

### Post by Ralph L on 2013-05-05
I am running ubuntu 12.04 Precise Pangolin latest update.  I have installed gnome-session-fallback.  I use "indicator-applet" in my task panel.  For some reason the spacing between the icons is excessive (takes up too much space on my single panel).  Can anybody tell me how to fix this??

Thanks in advance!

---

### Post by ibjsb4 on 2013-05-05
I use to have that problem when running a full indicator display.  Mine is modified these days and without that problem, but to answer your question.  Yes it can be fixed, I just do not remember the link that takes you to it.  So my apologies, I can only point you to here:

[https://www.google.com/search?client=ubuntu&channel=fs&q=excessive+icon+spacing+in+indicator-applet++gnome+classic&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=excessive+icon+spacing+in+indicator-applet++gnome+classic&ie=utf-8&oe=utf-8)

On a side note, do you know about this?

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

---

### Post by Ralph L on 2014-03-15
I still have the problem of excessive spacing of icons in Indicator-applet.  Has anyone found a solution?

---

### Post by Ralph L on 2014-06-12
If other people are annoyed that indicator-applet takes up so much space on a panel, please sign the petition at [http://www.petitiononline.com/buntubug/petition.html](http://www.petitiononline.com/buntubug/petition.html) .  It is old but so is the problem.  Very annoying on a small screen.

---

### Post by kansasnoob on 2014-06-13
You can reduce the overall size of 'indicator-applet-complete' by disabling "show-real-name-on-panel" and/or "user-show-menu" in dconf or by CLI, see:

[http://askubuntu.com/questions/87649/do-not-display-user-name-in-the-panel](http://askubuntu.com/questions/87649/do-not-display-user-name-in-the-panel)

Or you can reduce the size even further by swapping 'indicator-applet-complete' with 'indicator-applet':

[ATTACH=CONFIG]253921[/ATTACH]

Note: that example also displays 'caffeine' and 'indicator-sensors' which I use but are not absolutely needed.

More about that in step #2 here:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

---

### Post by Ralph L on 2014-06-20
kansasnoob

Thank you very much for responding!  I tried your suggestion of disabling "show-real-name-on-panel" and/or "user-show-menu" in dconf.  Doing so had no effect of shrinking (or growing) Indicator Applet on my panel.  Probably I have already taken out the referenced items.  But thank you--I am willing to try anything.

In the realm of trying anything, this site ([https://bugs.launchpad.net/indicator-applet/+bug/527267/+index?comments=all](https://bugs.launchpad.net/indicator-applet/+bug/527267/+index?comments=all) ) has code in post #88 to recompile Indicator Applet to squeeze out space.  It is for an older version of Ubuntu.  I tried recompiling on/for my Ubuntu 12.04 (Precise Pangolin) using it, but I got errors indicating that I didn't have the correct packages in my system--probably due to me having a newer system than the original poster had.  Any ideas on what to do to get this to compile--I am not very smart about packages and libraries.  It failed on the ./configure command.  See the attachment for the output of the ./configure command.

Thank you very much for your help.

---

