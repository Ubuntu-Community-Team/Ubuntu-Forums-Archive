---
title: "Docked too many gnome-pilots; opens many windows"
date: 2009-06-23
forum: Desktop Environments
---

### Post by djpandemonium on 2009-06-23
I'm trying to get my Palm to sync with Ubuntu 9.04.

The good news is that I followed the documentation, and it works.  The bad news is that it works a bit too well.

I followed instructions up the point that it said I needed to put the Pilot applet on a panel.  So, I tried to add it... but it wouldn't appear.  I tried a few more times, but the icon wouldn't appear on my panel.  I rebooted and tried again a few more times.  I tried dragging it in, double-clicking in the "add-to-panel" dialog, and a few other ways.

I was about to give up, but on a hunch I hooked up my Palm and hit the sync button... and it synced!  The problem is that, instead of opening up one dialog window that shows the progress of the sync, it seems to open up one for every time I tried to add the thing to my panel.  So, when I hit the sync button I get 20 or 30 dialogs.  The whole thing bogs down my system and slows everything down, until I close all but one of them.

Any idea how I can get rid of all the extras?  I am comfortable working at the command prompt, if I need to dig into something there...

---

### Post by djpandemonium on 2009-06-23
Got it.

If I open gconf-editor and navigate to:
/apps/panel/applets/
There are a whole bunch of applets titled applet_0 through applet_24.  All of them are for gnome-pilot.

I then used the command:
```
gconftool-2 --recursive-unset /apps/panel/applets/applet_*
```

---

### Post by newb85 on 2009-10-17
Thanks for posting the solution.  Saved me a lot of headaches.

---

