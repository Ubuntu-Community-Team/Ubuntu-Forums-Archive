---
title: "Laptop as second screen?"
date: 2012-08-24
forum: Desktop Environments
---

### Post by Halbblutplins on 2012-08-24
I want to use my laptop as a second screen for my pc. I know that there is VNC but there I can only see my current screen and its not working like a second screen.

Hope someone  can help me.

Peter

---

### Post by Kremlin on 2012-08-24
There probably isn't an easy way to do it seamlessly, but if both your laptop and the main computer are running linux, you can use the standard X11 networking interfaces to display things on the laptop screen. 
You can use something like [Synergy]("http://synergy2.sf.net") to share a main computer's mouse and keyboard between two computers (and a shared clipboard for copy-paste), and using the $DISPLAY environment variable, you can run apps from a main PC and display them on the laptop's screen. I'm afraid I don't know of any desktop environment/window manager that supports merging of two separate X11 servers into one environment, though, which is probably what you're looking for (essentially, to make the laptop a second screen for another computer).

---

