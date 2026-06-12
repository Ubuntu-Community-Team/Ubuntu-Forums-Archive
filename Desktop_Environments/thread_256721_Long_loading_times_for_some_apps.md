---
title: "Long loading times for some apps"
date: 2006-09-13
forum: Desktop Environments
---

### Post by dj_haruko on 2006-09-13
Yesterday, a few of my applications, such as gEdit, Evolution, the Gnome desktop, Tomboy, Monodevelop 0.12, and probably others, started to take a very long time to load up (like 3-5 minutes each).  Right before this happened, I had been VNC-ing into the computer (an Alienware Area 51-M laptop).  I usually use XFCE for my desktop, and when I VNCed in, I noticed that my icons were missing from all the tool bars.  That hasn't happened since, and VNC works like normal, but now certain applications take a long time to load up.

XFCE doesn't have this problem, nor does other XFCE-related programs, like Terminal or Mousepad.  Firefox, jEdit, Liferea, Gaim, and Ratpoison also do not have this problem.

The only thing I've changed recently is I've upgraded my version of Mono (1.1.17), which I keep in /opt rather than in /usr to keep it from messing with my directories.  That and the normal updates through the tray icon.

I get no out-of-the-ordinary error messages in the terminals when I run the applications from there.  Any ideas why these slowdowns are happening?

---

### Post by bswilson on 2006-09-13
It sounds like probably there is another program or background application using up your memory or something like that.  I would try opening a new terminal windows and running **top**.

Keep **top** going while you launch one of your problem applications.  Top updates I think every second, and you should be able to see which process is using up your RAM, processing power, etc.  This maybe will give you a view that a process needs to be terminated or killed.

---

### Post by dj_haruko on 2006-09-13
Did that that and the memory/CPU usage is just like normal.  I keep a monitor running in one of my toolbars.  The CPU never maxes out (it peaks at about 50% usually when loading one), the memory never goes above half, and I've never seen anything in my swap.

---

### Post by dj_haruko on 2006-09-13
I should mention that everything else runs at a normal speed, and the programs acting up also run at a normal speed after they load.  It's like they're trying to resolve something at startup, but timeout instead.

---

### Post by bswilson on 2006-09-13
Hmm, that is strange.  I'm afraid I've exhaused my troubleshooting abilities. Sorry I can't be of more help!  I'm sure some folks smarter than me will be able to help.

---

