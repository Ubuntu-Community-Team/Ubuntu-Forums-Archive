---
title: "A theme broke my desktop!"
date: 2006-09-27
forum: Desktop Environments
---

### Post by dwasifar on 2006-09-27
A while back, I loaded kubuntu-desktop on my Ubuntu installation and ran that for a while; switched back to Gnome today because it's faster and more stable.  But I like the look of KDE better, so I was poking around on gnome-look.org for themes that would make Gnome all pretty and shiny like KDE.

I downloaded and installed a theme called VistaBut.  As soon as I selected it in the theme manager, weird things started happening.  My taskbar clock crashed, then the weather applet.  I quickly found that other tasks just wouldn't start... including, wouldn't you know it, the theme manager.  And the terminal emulator.  I restarted X and it hung after the login, flashing the taskbar off and on.  I restarted X again and got the desktop to come up, but a lot of things were still broken.

In the end the fix was easy.  I went to the .themes folder (Nautilus being one of the things that still worked, thankfully), deleted the VistaBut theme, and restarted X.  The desktop came up with another random theme from the list, and I was able to get to everything again.  I had to reinstall the clock applet, though.  

I'm still trying to figure out what happened.  I don't know if the theme conflicted with the remaining KDE things that are still on my system, or what.  Or maybe just giving something a Microsoft name makes it buggy.

---

### Post by croak77 on 2006-09-27
Did you notice if you had a ~/.gtkrc-2.0? You might have had conflicting files setting your GTK theme. And it's not because of Microsoft name.

---

### Post by dwasifar on 2006-09-28
> **croak77 said:**
> Did you notice if you had a ~/.gtkrc-2.0? You might have had conflicting files setting your GTK theme. And it's not because of Microsoft name.
Yep, there it is, KDE comments at the top and all.  Guess I should kill that.  Thanks.

---

### Post by Josey on 2006-09-30
[http://www.ubuntuforums.org/showthread.php?t=262746](http://www.ubuntuforums.org/showthread.php?t=262746)

had the same problem

---

