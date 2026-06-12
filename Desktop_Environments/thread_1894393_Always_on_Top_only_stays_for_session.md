---
title: "Always on Top only stays for session"
date: 2011-12-12
forum: Desktop Environments
---

### Post by PaperPilot on 2011-12-12
If I set my clock applet for "Always on Top" it stays on top until I shut down the machine.  When I restart, the "Always on Top" bit is not set.  Must I set the "Always on Top" bit every time I start up?  Is there a way to keep this applet "Always on Top"?

I am running 64bit Ubuntu 11.10.

Paper

---

### Post by Krytarik on 2011-12-12
Of course those kind of tags are reset when you start a new session. But if you are using Unity or at least Compiz as the window manager, you can use its "Window Rules" plugin to set those permanently. Therefore, you'd need to install "CompizConfig Settings Manager" if you haven't already.

But stay away from "Preferences" in the lower left of its window, and don't try to enable the "Desktop Cube" without reading proper instructions before, as both can easily mess up your Unity!

Then in the "Window Rules" settings, to find the right "class" of your app window, "Grab" it through the dialog that comes up when you click the "+" button right of the "Above" field.

Here are more details reg. those 'Window Matches':

[http://wiki.compiz.org/WindowMatching](http://wiki.compiz.org/WindowMatching)

Regards.

---

### Post by PaperPilot on 2011-12-14
Krytarik:

Followed your instructions, but no joy.  The Windows Rules page of the CompizConfig Setting Manages says class=BuiciClock on the Above line.  When I started the computer this morning, the BuiciClock Always on Top bit was not set.

My Desktop Environment is Gnome Classic.  Does this make a difference?

Also while the Always on Top bit is set for the BuiciClock, child windows opened by say Evolution, open on the bottom.  After the bit is cleared, the child windows open on top, but the BuiciClock is not displayed.

I am now more confused than before I changed the Compiz settings.

---

### Post by Krytarik on 2011-12-14
> **PaperPilot said:**
> My Desktop Environment is Gnome Classic.  Does this make a difference?
Yup, since it doesn't use Compiz by default. ;-)

But if you want it to do so, please see this guide:

[http://www.tuxgarage.com/2011/10/running-gnome-classic-with-compiz.html](http://www.tuxgarage.com/2011/10/running-gnome-classic-with-compiz.html)

---

### Post by PaperPilot on 2011-12-16
Adding Compiz worked.  Thanks a lot.

---

