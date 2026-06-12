---
title: "Gnome vs XFce - help with one feature"
date: 2005-08-03
forum: Desktop Environments
---

### Post by Rug on 2005-08-03
I love XFce, and want to run it all the time, but there is one feature that Gnome uses that I want.

With Gnome as the DE, I can use the scroll-wheel over a non-active window and scroll it without making it active (and therefore it doesn't steal focus from a foreground-window.

I primarily use this when coding.   I have a web-page open (non-active, background) and a term-window (active, foreground);  so I can type away in the term, move the mouse up to the browser, and scroll the screen.

Is this possible in XFce?  As a side-bonus I find that Gnome's auto-mount (not auto-run, I hate that too)  more reliable then mounting in XFce, but that is not a deal breaker.

---

### Post by psychicdragon on 2005-08-03
I think you'd have to replace xfwm4 with something else (possibly even metacity) to solve the first problem.

Your second problem can be solved by adding gnome-volume-manager to your Xfce session. You can turn off the auto-run features through the gnome-volume-properties applet.

---

