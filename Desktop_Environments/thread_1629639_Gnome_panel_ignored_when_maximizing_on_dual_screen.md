---
title: "Gnome panel ignored when maximizing on dual screen."
date: 2010-11-24
forum: Desktop Environments
---

### Post by MForey on 2010-11-24
I have searched long and hard for an answer to this one, only to discover that this is apparently a long-standing, unresolved bug.  Therefore, I am looking for some sort of workaround that resolves the issue without having to revise my desktop layout in the process.

I am running a dual monitor setup through nVidia's TwinView setting.  The primary monitor is 1600x900, secondary is 1440x900, and the secondary is placed to the right of primary.  I am running Lucid with the compiz window manager.

On the primary monitor's portion of the screen area, I have a right- and bottom-side panel, and the secondary monitor has only a bottom-side panel.  When maximizing applications on the primary monitor, the bottom-side panel area is taken into account and the vertical resize ends there.  However, the application maximizes underneath the right-side panel to the monitor's full horizontal dimension and thereby becomes partially obscured.  The issue, as best I can tell, is that the window manager does not recognise a panel that is officially positioned in the center of the X screen as being a boundary despite it being linked to the right edge of the monitor, which does qualify as a boundary.

Causing the application to maximize over the panel is not an acceptable solution, as it denies me access to the utilities I have set up there.  The so-called "autohide" is also unacceptable, as that simply causes the panel to drift onto the secondary monitor and then enter a loop where it flips back and forth between monitors when I attempt to access it.

Any assistance that can be provided would be greatly appreciated.

---

### Post by jakon on 2010-12-12
You probably have found it already, but, this is [https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/58977](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/58977) . I stopped using the maximise button because of this... Sad...

---

