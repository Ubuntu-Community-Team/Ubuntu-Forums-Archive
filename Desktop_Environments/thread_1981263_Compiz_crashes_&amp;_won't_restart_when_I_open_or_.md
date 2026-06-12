---
title: "Compiz crashes &amp; won't restart when I open or close maximised windows"
date: 2012-05-16
forum: Desktop Environments
---

### Post by beccatoria on 2012-05-16
I upgraded to 12.04 recently and I haven't been able to get Compiz to work properly. I have a laptop with an integrated Intel graphics card.  

At the moment, Compiz works fine unless I: 

1) Close a maximised window.  
2) Open a program that will open as a maximised window.  

If I maximise a smaller window, it's fine.  If I close a smaller window, it's fine.  

When I do either of the above, compiz grinds to a halt, the screen freezes, goes black for a moment, then reloads without window decoration.  

Using the terminal to restart gtk-window-decorator hangs and does nothing.  Running compiz --replace restarts compiz and everything looks great for about half a second before the graphics become horribly corrupted (trails of wallpaper following moved windows/panels only visible when you "paint" your mouse over them levels of corrupted).  The terminal tells me that it failed to "bind image to texture".  Logging out and back in doesn't really fix it either, I need to reboot.  

For background information, when I originally installed 12.04, I couldn't get compiz to work at *all* and think I was suffering from [this]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/980017?comments=all") bug, and I still get the apport error message semi-frequently, though it doesn't seem to precipitate any changes in the display.  Installing the xorg-edgers ppa improved the situation to the point I'm at now.  

Any help would be deeply appreciated.

---

### Post by wilee-nilee on 2012-05-16
Fix put in 5/14 you updated? Not sure that is your bug though, if you are running unity and tweak compiz incorrectly it is a bit funky.

---

### Post by beccatoria on 2012-05-16
I'm not sure if you're referring to the fix for the bug I referenced as a background issue?  In which case, yes, I updated via xorg-edgers and noticed an improvement, which is part of why I'm not 100% certain that what I'm experiencing now is still part of that issue.  I just wanted people to be aware that I had xorg-edgers enabled and why, in case it was relevant.  

I also have -proposed enabled and didn't see any mesa updates, but that could be because I already installed the relevant stuff via xorg-edgers.  

With regards to your other point, I actually run Gnome Classic desktop by choice, and the issue is constant in either Unity or Gnome.  I do have Ubuntu Tweak installed but have not used it for anything except cleaning up old package files, I haven't used it to change any compiz settings.  Would uninstalling it be a wise option?  Is that something that could conceivably be causing this?  I'm pretty dire when it comes to understanding the technical aspects of Ubuntu, so seriously, any help is appreciated.

---

### Post by beccatoria on 2012-05-17
Bump?  :)

---

