---
title: "netbook remix but not maximized windows on load"
date: 2009-04-15
forum: Desktop Environments
---

### Post by adonis827 on 2009-04-15
Hi!

I have the netbook remix on my msi wind. Each time you open a new window, it is maximized by default. I prefer if it is unmaximized. 

I am wondering if it is possible to set it somewhere.

Thanks!

---

### Post by njpatel on 2009-04-16
> **adonis827 said:**
> Hi!

I have the netbook remix on my msi wind. Each time you open a new window, it is maximized by default. I prefer if it is unmaximized. 

I am wondering if it is possible to set it somewhere.

Thanks!

You can either stop Maximus from starting (this is what maximises and undecorates your windows), OR you can tell maximus to not maximise windows be default.

To stop maximus from running at startup, Preferences->Startup Applications, and uncheck "Maximus Window Management" from the "Addition Startup Programs" list.

To tell Maximus to not maximise windows by default (but continue to undecorate windows that you maximise), run:

gconftool-2 --set /apps/maximus/no_maximize --type BOOL true

in an terminal.

You'll need to reboot or logout/login for the settings to take effect for both options.

Hope that helps,

Neil

---

### Post by adonis827 on 2009-04-30
> **njpatel said:**
> You can either stop Maximus from starting (this is what maximises and undecorates your windows), OR you can tell maximus to not maximise windows be default.

To stop maximus from running at startup, Preferences->Startup Applications, and uncheck "Maximus Window Management" from the "Addition Startup Programs" list.

To tell Maximus to not maximise windows by default (but continue to undecorate windows that you maximise), run:

gconftool-2 --set /apps/maximus/no_maximize --type BOOL true

in an terminal.

You'll need to reboot or logout/login for the settings to take effect for both options.

Hope that helps,

Neil


Sorry for the really late reply. the gconftool-2 command did not work. but removing maximus from preferences -> sessions -> startup programs did work. Thank you very much Neil you have been of big help. I might try out 9.04 + netbook remix on my wind soon.

---

### Post by marleo on 2009-05-11
To leave maximus running but stop it from maximising new windows by default, you can use the graphical gconf-editor tool.

Use ALT+F2 to bring up a run box, type in gconf-editor and hit enter. You can then browse to Apps - Maximus, or use Edit - Find (or CTL-F) and search for no_maximize - you need to check the "search in key names" box. Once you've got the Maximus settings in the right panel, you can check the no_maximize option.

---

### Post by djst on 2009-07-24
Just wanted to say thanks for the help in this thread! The maximize by default option is what made Netbook Remix a true annoyance -- checking the no_maximize option turned it into something really useful instead.

Is there any way to make maximize appear more like the normal window borders -- that is, double-clicking to unmaximize, and showing minimize and restore buttons next to the close button?

---

