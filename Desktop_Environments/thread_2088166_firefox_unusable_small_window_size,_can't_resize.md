---
title: "firefox unusable small window size, can't resize"
date: 2012-11-25
forum: Desktop Environments
---

### Post by kosmos on 2012-11-25
Ubuntu 12.04, kernel 3.2.0-33-generic...
Just did a "apt-get upgrade" and firefox broke. It now starts up with a tiny window that is unusable and which cannot be made bigger. I use a custom desktop based on plain ubuntu, using the Sawfish window manager, which has been my WM of choice for years.

Here is a screenshot of the firefox window:
[http://imgur.com/A9TDW](http://imgur.com/A9TDW)

That's as big as the window gets. F11 doesn't make it bigger. My keyboard shortcut to maximize the window doesn't make it bigger. Can't drag a corner to make it bigger. Started in safe mode and with a brand new firefox profile and the same results. All other apps behave normally with respect to window sizing.
Screen resolution is 1920x1080. 
Firefox version is: 17.0+build2-0ubuntu0.12.04.1

When I switch from sawfish to the regular gnome window manager, then firefox does start up with a normal window and is resizable.

---

### Post by personalpc on 2012-11-25
try dpkg-reconfigure firefox

also make sure compiz or gnome-settings-daemon is not running in the background and maybe consider chromium which does much better in minimal x environments. Also there is Epiphany and others.

---

### Post by kosmos on 2012-11-25
> **personalpc said:**
> try dpkg-reconfigure firefox
Didn't seem to do anything.

> also make sure compiz or gnome-settings-daemon is not running in the background 
They are not running.

> and maybe consider chromium which does much better in minimal x environments. Also there is Epiphany and others.

I've started using chromium, but the problem is that I've spent a great deal of time customizing firefox with the addons I like, and it's a huge pain in the rear to switch to an unfamiliar browser. I think I'd like to stick with firefox, for it's features and greater configurability.

---

### Post by VooDooSyxx on 2012-11-25
Instead of apt-get upgrade give apt-get dist-upgrade a try. If that does not immediately resolve it, I would remove and reinstall firefox. It shouldn't mess with your settings at all since those are all stored in $HOME/.mozilla.

---

### Post by kosmos on 2012-12-07
I've concluded that the problem is that somebody broke the sawfish window manager in a big way, it's virtually unusable in quantal. I've switched to awesome window manager for now, which does not exhibit the same problem.

---

