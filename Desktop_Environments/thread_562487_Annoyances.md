---
title: "Annoyances"
date: 2007-09-28
forum: Desktop Environments
---

### Post by Termina on 2007-09-28
I was wondering if someone could help me out with a few 7.04 annoyances I have.

The first is that, when saving an image with firefox, when I double click on 'Desktop' on the left side of the save box my image name is cleared (blanked). This is very annoying, since I like to be able to navigate to different directories, but would like to keep the filename.

The second annoyance is that, assuming I have two windows (or a window and a program) open, I would like to be able to click on a file in order to drag it without bringing it to the front of the screen.

My last is that in 7.04 (as seen by the bugs in launchpad) there is no way to disable the switch user option in Gnome. I know debian has the same problem, but this is a real annoyance. :/

---

### Post by Wolki on 2007-09-28
> **Termina said:**
> The second annoyance is that, assuming I have two windows (or a window and a program) open, I would like to be able to click on a file in order to drag it without bringing it to the front of the screen.

Yup, that's quite annoying. You can prevent raising the window by holding a modifier key (Ctrl, Shift, and depending on your configuration Super/WinKey - Alt won't work as Alt-Left Mouse Button moves windows) when you start dragging. Some of these will change what dropping does, so release them before dropping if you don't want that.

You can also hover over an entry in the window list while dragging to raise that window (and over a workspace to switch to that workspace).

One more thing you could do is disabling "raise_on_click" which means that windows won't get raised anymore when you start to drag - but they also don't get raised when you click them anywhere but the title bar.

Here's the relevant GNOME bug: [http://bugzilla.gnome.org/show_bug.cgi?id=80984](http://bugzilla.gnome.org/show_bug.cgi?id=80984) The developers would be interested in solving this, but it's a complex issue and there aren't many people developing metacity, the GNOME window manager; so I wouldn't hold my breath.

[edit] Can't help you with the other ones. Why do you want to disable switch user though, instead of simply not using it?

---

### Post by llamakc on 2007-09-28
Why not just uninstall fast-user-switch-applet?

---

