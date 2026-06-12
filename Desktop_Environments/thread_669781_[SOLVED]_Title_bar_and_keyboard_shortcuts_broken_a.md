---
title: "[SOLVED] Title bar and keyboard shortcuts broken after auto-update"
date: 2008-01-16
forum: Desktop Environments
---

### Post by clmw on 2008-01-16
Hi.
After one of the recent auto updates several problems developed with my system:
1) The title bar on all my windows lost the minimize, maximize and close icons at the top right (and the icon that is normally in the top left was moved to the middle of the title bar)
2) My shortcut keys, particularly alt-tab and ctrl-alt-arrow (to switch workspaces) stopped working.  However ctrl-alt-F1 to go to a terminal still seem to work.  It seems to only be the ones relevant to the window manager that aren't working
3) The repetition of keystrokes was disabled

#3 was an easy fix through System->Preferences->Keyboard

I was also able to fix #1 by looking through other posts of people with similar problems and I used gconf-editor to edit the configuration for apps->metacity->general->button_layout and set the value to menu:minimize,maximize,close

However, I still have not been able to fix problem #2.  I can't seem to find any way to get my alt-tab and other shortcuts to work.  I've tried deleting all my .gnome, etc. and creating a new user and the problem persists.  I've also tried reinstalling gnome and metacity with synaptic and still no joy (well, no alt-tab...).

Does anyone have any idea what could be causing this?  I included the other two problems that developed under the assumption that one thing getting corrupted could have been the cause of all three problems and that my solutions to the other two were just workarounds...

Oh, and I'm using 7.10 with GNOME and metacity (sadly my laptop doesn't seem to like compiz).

Any help would be more than welcome!

---

### Post by clmw on 2008-01-16
Fixed!  For those who are interested, it seems to have been gtk that was the offending member.  I went through and reinstalled every package named gnome* libgnome* metacity* and gtk* and everything works now!

---

