---
title: "Firefox on Feisty: No window coming up"
date: 2007-04-29
forum: Desktop Environments
---

### Post by rainerf on 2007-04-29
Hi all!

I switched to Feisty just today, but I encountered a problem with firefox. It was working fine while I was running the Live System, but on the installed system, after starting it, no window comes up. A process is running, but no window, no entry in the task bar or whatever are to be found.

I tried removing .mozilla, reinstalling firefox, rebooting, but all to no avail. It also seems to be independent of the window manager since it happens in both gnome and e17.

What's even more puzzling is that I encountered the same thing in Gentoo before installing Feisty today..

Any ideas, anyone?

I posted an strace log at [http://rainer.findenig.net/pub/ff](http://rainer.findenig.net/pub/ff) but I was unable to find anything in there.

Thanks in advance!
Rainer.

---

### Post by rainerf on 2007-04-30
Back again, with a few updates:

* I can see dialog windows from firefox (eg. the "start new session" or "restore last session" dialog), but not the main window.
* The very same thing happens with Thunderbird.
* It only happens while I have a dual-monitor-setup enabled. After urning the second one off (using xrandr), Firefox comes up just fine (and so does Thunderbird), although the dpi are obviously incorrectly set then, since all fonts are way too large.

Thanks for any input or even ideas where I could keep looking...

---

### Post by colonelk on 2007-05-01
I have the same problem and need a fix.

---

### Post by Seculus on 2008-03-14
I had the same problem.  I was able to get firefox to work again by changing the resolution in System->Preferences->Screen Resolution.

The problem appeared after I started using the ATI fglrx driver.  Apparently my screen resolution was set to 2800x1050 --- I had been using a dual monitor setup earlier.

This was a very annoying problem since no error message was displayed.  The firefox window simply did not appear.

Again, the solution in my case was simply to change the resolution.  If that doesn't work for you, consider either not using the fglrx driver or manually installing the latest version of firefox.  Both of these approaches are problematic, of course.

---

