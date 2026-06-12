---
title: "No TRASH Launcher/Icon in Classic/Fallback Since 12.10 Upgrade. Can I Get It Back?"
date: 2012-10-26
forum: Desktop Environments
---

### Post by OzzyFrank on 2012-10-26
Since upgrading to 12.10 last night, I've been missing the Trash icon at the far-right of my bottom panel (I'm of course using Gnome 3 "Classic"/Fallback-Mode, in 64-bit). If I had a Trash icon on the desktop before, there isn't one there now (since there are none of my launchers are there at all now, possibly due to the fact that after upgrading, I no longer had a file manager: [http://ubuntuforums.org/showthread.php?p=12320238#post12320238](http://ubuntuforums.org/showthread.php?p=12320238#post12320238)).

I can access **Add to Panel**, and **Trash** is there, but I simply cannot add it to either of the panels. I can add other things, like the Workspace Switcher, but not Trash.

Not sure if it is at all related to my window managers/decorators being a tad screwy since the upgrade ([http://ubuntuforums.org/showthread.php?p=12320320#post12320320](http://ubuntuforums.org/showthread.php?p=12320320#post12320320)), but I'm guessing there has to be a way to access the trash, other than by doing so in the left-pane of Nautilus (which I manually installed after the upgrade [3.4.2], and the system has since updated [3.6.1]).

Any ideas?

---

### Post by OzzyFrank on 2012-10-31
OK, I had a look around in *Dconf Editor* and noticed in **org > gnome > gnome-panel > layout > objects** there were 8 instances of **TrashApplet** (I tried 7 times to add it again via *Add to Panel*), and changing the values did nothing. So then I thought I'd do a search for "trash" in *Synaptic*, and noticed straight away that the package **[COLOR="Red"]gnome-applets[/COLOR]** was not installed, even though some of the applets were working fine on my panels.

So I simply installed **gnome-applets**, did a **[COLOR="Red"]killall gnome-panel[/COLOR]**, and suddenly 8 trash icons (and 2 system monitors) appeared at the right end of my bottom panel. So seems the 12.10 upgrade did something wacky and removed that package, but it's easily rectified.

---

