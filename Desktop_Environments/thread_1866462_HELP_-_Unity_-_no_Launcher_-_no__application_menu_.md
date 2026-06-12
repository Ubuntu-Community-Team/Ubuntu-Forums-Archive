---
title: "HELP - Unity - no Launcher - no  application menu bar"
date: 2011-10-21
forum: Desktop Environments
---

### Post by igouy on 2011-10-21
I had a working 11.10 x64 install, upgraded in place from 11.04

In an attempt to stop the windows snapping to the right-hand-side of the display, I used synaptic to install compizconfig-settings-manager.

I opened compizconfig-settings-manager and looked around but couldn't see how to do what I wanted.

I closed compizconfig-settings-manager.

Now there's no Launcher.  Now the only menu bar is the desktop menu bar.

I've tried: unity --reset :but that gives warnings and then hangs.

   ...
   unity-panel-service: no process found
   ...
   ...
   comprize (core) - Warn: failed to receive ConfigureNotify event on 0x1c00bcb


Please what can I do to fix this problem from a terminal window (which is all that seems available ctrl-alt-t).

---

### Post by Copper Bezel on 2011-10-21
Oh, good, I'm glad you can still get to a terminal window. Otherwise, you'd need to type this by hand.

Run 


```
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
rm ~/.compiz-1/session/*
rm ~/.config/compiz-1/compizconfig/config
```

Then unity --reset. Should fix it right up. Instructions [from Tux Garage]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html").

To disable window snapping in CompizConfig, untick the Grid plugin under Window Management.

---

