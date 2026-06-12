---
title: "Specifying which workspace to load into"
date: 2011-10-17
forum: Desktop Environments
---

### Post by paskari on 2011-10-17
This question was [asked a while back ]("http://ubuntuforums.org/showthread.php?t=1128091") and I have also asked about it on [askUbuntu]("http://askubuntu.com/questions/68354/is-there-any-way-to-specify-which-workspace-and-or-window-to-launch-a-program-in"). I am surprised there is not an easy way to do this.

As I point out in the askUbuntu forum, wmctrl is NOT a good option, as it has serious problems. Is there a better solution out there?

The biggest problem I have with wmctrl is that the command line and the window manager don't communicate very well. Window names are not guaranteed to be unique, window IDs are difficult to obtain, and the fact that the control is returned to the command line BEFORE the window is launched, makes it hard to guess which is the most recently launched window.

---

