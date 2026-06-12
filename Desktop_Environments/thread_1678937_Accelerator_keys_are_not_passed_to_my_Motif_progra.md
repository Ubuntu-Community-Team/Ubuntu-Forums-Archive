---
title: "Accelerator keys are not passed to my Motif program."
date: 2011-01-31
forum: Desktop Environments
---

### Post by felix-fi on 2011-01-31
I have an old Motif program which works perfectly well under Ubuntu 10.4, except for one annoying thing: the accelerator keys used to activate some menu items are not working.

The exact same program works perfectly well under Fedora Core 12, but not under Ubuntu 10.4.

These keys are defined using XmResource:

*addFactGoal.labelString: 	Add Fact or Goal
*addFactGoal.accelerator:		Ctrl <Key>A
*addFactGoal.acceleratorText:		Ctrl-A

This is not an X11 problem as the program works fine if I start with an Xterm session and launch the program from the xterm. It seems to be caused by Gnome window manager...

Any idea? 

Thanks in advance,

---

