---
title: "Manually compiled pidgin-libnotify and indicator applet"
date: 2010-11-22
forum: Desktop Environments
---

### Post by salami on 2010-11-22
Hi everyone

I'm new to this forum, please excuse me if I didn't find this already answered somewhere ;)

I have pidgin installed from source and want to get notifications through the indicator applet. Obviously I need the plugin "pidgin-libnotify" for that (which works perfectly fine when installed from the ubuntu package on a second machine). But in order to keep my source install (and not cause broken package dependencies) I'm trying to get pidgin-libnotify to work from source too, with little luck.

The "Indicator Applet Session" sees pidgin and allows me to set my status through it, but the "Indicator Applet" doesn't seem to be aware of my pidgin-libnotify and it doesn't show notifications (they show up as pidgin pop-ups).

Does the official pidgin-libnotify package do any additional configuration that I have to manually add?

Thanks for any hints!

---

### Post by salami on 2010-11-23
Well I had a look at the package source and noticed that it has patches applied that allow that integration and is not based on the original source code, so I will have to use the ubuntu version (or apply the patches to the source manually).

I extracted the plugin file from the official deb package manually so apt doesn't get all upset about the dependencies, works perfectly :)

---

