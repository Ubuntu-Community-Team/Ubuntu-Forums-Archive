---
title: "Urban Terror switches to windowed mode"
date: 2009-04-25
forum: Gaming &amp; Leisure
---

### Post by Jesus on 2009-04-25
When playing Urban Terror in Gnome, after a few minutes the game always switches from fullscreen to windowed mode. When this happens I also lose input, both to the game and to Gnome. The only thing I can is ctrl-alt-f1 to switch to a console and kill the process. I suspect it may be gnome-screensaver trying to kick in. If this is the case I'd prefer not to disable gnome-screen entirely, but I will if necessary. Does anyone recognise this issue and can suggest a solution?

---

### Post by 5nak3 on 2009-04-25
You are most likely running compiz in the background. There are a number of threads on this issue in the forums:

[http://ubuntuforums.org/showthread.php?t=1121185](http://ubuntuforums.org/showthread.php?t=1121185)

However the problem essentially boils down to:

you are running compiz (fancy desktop effects)

Click applications -> add/remove -> type in "compiz fusion icon" select the program and install it.

Now before you play urbanterror:

Click applications -> system tools -> compiz fusion icon -> the compiz icon should load up in the top taskbar.

From there

Right click the icon -> select window manager -> select metacity and you are good to play urban terror without any minimizing.

If you want compiz back after, just right click the icon -> select window manager -> select compiz -> right click the icon again -> reload window manager

And you're done.

Hope that helps

If this does not help please post with a few more details, system specs, card type, any power management options and someone may be able to give you a better answer. Good Luck!

---

### Post by steelblue77 on 2009-05-30
THANKS!  I love these boards!

---

### Post by Amof on 2009-05-31
[http://ubuntuforums.org/showthread.php?t=1157516]("http://ubuntuforums.org/showthread.php?t=1157516")

---

