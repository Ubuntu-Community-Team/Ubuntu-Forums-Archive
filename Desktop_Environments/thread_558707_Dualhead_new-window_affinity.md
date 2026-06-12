---
title: "Dualhead new-window affinity"
date: 2007-09-24
forum: Desktop Environments
---

### Post by miamicanes on 2007-09-24
I'm running dual-head with a notebook (Dell D600) and external display. I'm using the 'radeon' driver to handle the dualhead operation, and have it configured to use the external display as my 'main' one (the one where the Gnome desktop gets rendered). The problem is, just about every program I launch ends up opening in the other pane (the one corresponding to the laptop's internal display). Netbeans gets it right, but Firefox 2, Terminal, and gedit (just to name 3 that I run a lot) all insist on opening new windows on the wrong side.

I guess I have a few specific issues to resolve:

* How, exactly, do I establish which display is the 'main' one (where kde should render its main icons, and where new application windows should open)?

* Is there a way to tell apps like Firefox, etc, "Open by default in the 'main' display, but if you're already open and physically running within the 'other' display, open new windows THERE instead.

Since it probably matters, I'm using the 'Radeon' driver's built-in dualhead support (I hated the way Xinerama LITERALLY tried to treat it like one big display, and annoyingly opened new windows centered between the two displays). I work mostly in the main display, and tend to use the other one for things like open pdf documents, IM clients, etc.

---

### Post by toon on 2007-09-26
Hello,

Perhaps [http://ubuntuforums.org/showthread.php?t=560322](http://ubuntuforums.org/showthread.php?t=560322) might be of interest to you (or specifically [http://ktown.kde.org/~seli/xinerama/](http://ktown.kde.org/~seli/xinerama/)).

Also, theres [http://lists.kde.org/?t=109658240300002&r=1&w=2](http://lists.kde.org/?t=109658240300002&r=1&w=2)

---

