---
title: "Kubuntu Composite Problem"
date: 2006-09-22
forum: Desktop Environments
---

### Post by blip on 2006-09-22
I've been experiencing a peculiar problem.  I use composite shadows and transparencies in KDE and innitially they work great on my Pentium D 3 Ghz  with Nvidia 7300 GS.  After an hour or two, however, a bunch of problems begin to occur.  Suddenly the transition between levels of transparency become agonizingly slow.  If I try to move a window around it leaves ghosts of its decoration throughout the screen.  Occasionally the computer seems to get confused about which window is on top of the other. (i.e. parts of background windows suddenly appear in the foreground.) Xorg suddenly consumes 50% or so my procesor time while idle (normally the system idles at 1 or 2% ). Thankfully a quick restart of Xorg fixes the problem, for another two hours or so.

From what I've observed it seems like the problem generally occurs when I have a lot of windows open. Also decreasing the number of effects used seems to increase the amount of time between incidents. 

This may just be a flaw in the compositing manager (which I could stop using... but it's so pretty! :) )... It may also be something that has already been addressed (though a quick search didn't turn up anything quite like this)... but does anyone have any advice about how I might trouble shoot this? Thanks!

---

### Post by RAOF on 2006-09-22
It's probably an bug in the interaction between your graphics drivers and the Composite extension and KDE's composite manager.  Composite managers are (relatively) new, and quite prone to bugs/graphical artifacts.  If you wanted to trouble-shoot, you could probably watch the RAM utilisation of Xorg and/or kwin.  Odds are, there's a memory leak in the composite code somewhere, and the memory usage will steadily increase.

Also possible is there's a memory leak in the **texture** memory code, so you're graphics card's memory is being filled.  I've got no idea how you could check that, though.

---

### Post by blip on 2006-09-23
Good thoughts.  I watched memory utilization and it does not increase with the problem occurs so it is probably on the video card side.

I do have good news though, I downloaded the version of nvidia-glx that hit the repos a few days ago and the problem has improved significantly.  Now it seems like I can run xorg for 4-5 hours without noticeable problems.  When they do occur they are far less severe.  So it looks like things are at least bearable now.

---

