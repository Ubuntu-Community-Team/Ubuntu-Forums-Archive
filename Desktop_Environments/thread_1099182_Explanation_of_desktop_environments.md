---
title: "Explanation of desktop environments"
date: 2009-03-17
forum: Desktop Environments
---

### Post by Volt9000 on 2009-03-17
I'm trying to wrap my head around something.
Gnome, KDE, Xfce and whatever else are different desktop environments. What exactly does this mean? Does this refer to the visual aspect of windows, controls, etc. or does it go deeper than that?

I only ask because up until recently I thought it *did* go deeper than that... that it was some kind of graphical protocol, for lack of a better term. I was under the impression that you can't run KDE apps in Gnome, and vice-versa, but apparently you can.

Could someone please explain or point me to an explanation as to the what it means to have these different desktop environments?

---

### Post by Locutus_of_Borg on 2009-03-17
A desktop environment is basically the graphical interface.  usually a full DE will include stuff like a utility to draw the desktop, with support for desktop icons, a toolbar/status bar, file manager, and window manager, along with some other tools

"KDE apps"  simply refer to applications that use the QT library, while "GNOME apps" use the GTK library, just different means of rendering objects.

There are also window managers that can be run without a desktop environment.  They simply provide a means to display windows, usually with some kind of window decorations.

For instance, i do not run a desktop environment, but rather just a window manager.  I use different applications for such things as making my background an image, I dont like icons, so i do not use anything to allow icons to be displayed, and separate apps for file management, panels, etc.

You can run any WM within any DE, but you cannot run two WM's together.  Example: compiz is a WM, it can run with GNOME, KDE, or by itself, but cannot be run with Openbox since Openbox is another WM

---

