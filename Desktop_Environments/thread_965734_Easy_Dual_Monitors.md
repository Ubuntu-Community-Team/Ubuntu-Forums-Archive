---
title: "Easy Dual Monitors?"
date: 2008-10-31
forum: Desktop Environments
---

### Post by Heroshinator on 2008-10-31
Is there any program like ultramon for linux so that the dual monitor process is easy. Im using a 20" and a 15".

Edit: Using a Nvidia 8800 GTS and have Nvidia X Server Installed

---

### Post by utnubuuser on 2008-11-02
Hi -  Which version of Ubuntu are you in?  I've been uing 8.04 since it was released, and I tried to follow the dual monitor tutorial in "General  Questions", without much luck, I've also got 8.10 installed, plugged my second monitor in, turned on my laptop, went to System>>Preferences>>ScreenResolution  -- clicked 'detect displays', and got a mirrored screen (though it showed only one screen in the picture box).  unchecked 'mirror display', dragged the laptop screen to the left, which gave me a view of the second screen hiding under the laptop screen (called 'unknown'), clicked apply, at which point a dialog box open saying xorg needed to change the default resolution to create a virtual resolution equalling the sum of both displays, clicked ok/apply, was told to log-out and then log in again, and presto, dual monitors.  Now this is just a laptop though, and I know with Nvidea it might be different.
8.04 uses the same application as diplay/resolution manager, but never offered to rewrite the xorg.conf file.
8.10 is looking good.

---

### Post by xv1700 on 2008-11-17
I have just configured it all via "Screen Preferences" but only after running:

"xrandr --output VGA --off"

---

