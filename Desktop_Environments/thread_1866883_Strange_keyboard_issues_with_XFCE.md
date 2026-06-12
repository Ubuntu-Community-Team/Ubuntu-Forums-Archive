---
title: "Strange keyboard issues with XFCE"
date: 2011-10-22
forum: Desktop Environments
---

### Post by Svip on 2011-10-22
I have an unusual monitor set up.  I have a two DVI-output graphics card.  Each monitor is the exact same dimensions.  *But* the right monitor is 90 degrees on the side ('CCW' in **xorg.conf** terminology or 'left' for **xrandr**).

This is a setup neither Xinerama nor TwinView can figure out to handle correctly, as both tries to consider both screens as one X screen.  Which means, if I try to rotate it, *both* screens rotate, which is obviously undesirable.  However, disabling Xinerama *and* TwinView made gnome-panel and Unity crash upon arrival.

I decided that there was nothing wrong with my X setup, but something wrong with gnome-panel and Unity, and decided to go for Xfce instead.

Pleased, Xfce had no problems with the setup.  But instead it presented me with a stranger problem.

I use a setup as well, that allows me to toggle between two keyboard layouts via Caps Lock; us altgr_intl and dk.  That requires either an Xorg.conf configuration or xfce-xkb-plugin.  I went for the latter.

And while initially the setup worked, I noticed a strange behaviour by the non-alphanumeric keys (e.g. page up/down or the arrow keys), that they were suddenly binded to another key instead.

At first the up key was print screen (confirmed by xev), but later page up became context menu and page down was insert, while home and end and the arrow keys did nothing.

I realised, amusingly, that the fix is simply to select another keyboard model from the Xfce's Keyboard settings, then everything functions again.  But once I try to enter the xfce-xkb-plugin window, the keyboard reverts to its 'unusual mode', which then requires the re-selection as a fix.

This is mildly annoying, as I do quite often use these keys.  And after numerous tries, I am still not certain what the problem is.

However, I may have an idea.

For the record, I use the following input devices:

* Das Keyboard Ultimate 105-key layout.
* Logitech mouse which version I forget (it's 9 years old).
* Wacom Bamboo
* Cyborg R.A.T. 7

The latter specifically is of interest as I know it has an issue with X.  However, for the last year, this was confined to *one* issue (focus) and it had a simple solution: just restart X once the problem occurred (easy to reproduce), and it will never occur again until you restart.

I wonder if the driver issue related to the mouse might be causing some strange behaviours for the keyboard.  But at the same time, I never had odd functionality with the keyboard under Gnome2, gnome-panel and Unity (the latter two had other issues, and the former I cannot have because it is no longer 'supported' even though I *know* it works).

For now, I am forced to keep the keyboard settings window open at all times, whenever the issue arises again (it has become quite unpredictable at this point, it almost seems like it is timed or something).

Quick aside: Is it possible to tell Xfce to turn off the monitors when it goes into blank screens?

---

### Post by gsmanners on 2011-10-22
I don't know about the keyboard issues, but the Screensaver can do Power Management (in its Advanced tab). That has Standby, Suspend, and Off for the display.

---

### Post by Svip on 2011-10-22
Thank you, that worked.  Speaking of screensaver, how come the screensaver is still activated while I watch mplayer?  I use the mplayer from the Medibuntu repo, btw.

---

### Post by gsmanners on 2011-10-22
I've never had trouble with screensaver interfering with mplayer. Anyway, you might want to use mplayer2 from the repos at this point.

---

### Post by Svip on 2011-10-29
Well, removing xfce4-xkb-plugin and moved the functionality into xorg.conf solved the issue.  So that's solved.

---

