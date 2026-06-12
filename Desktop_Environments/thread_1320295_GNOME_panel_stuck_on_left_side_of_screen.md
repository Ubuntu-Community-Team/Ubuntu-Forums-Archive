---
title: "GNOME panel stuck on left side of screen"
date: 2009-11-09
forum: Desktop Environments
---

### Post by Veovis Muad'dib on 2009-11-09
==========
My system:
==========
Ubuntu 9.10 x64, up to date, less than a day of configuration old.
Dual booting with Windows 7 x64.
Running GNOME with Compiz effects.

==================
How this happened:
==================
I was playing with making an application launcher panel, not Expanded, on the bottom left corner, and a window list, again not Expanded, on the bottom right corner, both of which were set to auto hide.  I then set the top panel to always show and to hold all of my information I want to always see.  I played with this, and decided that maybe the application launcher might look good on the left side, so I set it to do that.  It didn't look good, so I tried to reset it to the bottom, but I was unable to even get the panel to pop out, let alone get into preferences.

==============
What is wrong:
==============
There is a small, autohiding GNOME panel on the left edge of my screen, that will not pop out, and that I cannot remove.  It is annoying because a one pixel edge is sticking out, and when moving the desktop cube, it looks rather bad.

==================================
What I have tried to do to fix it:
==================================
[LIST]
[*]I have tried hovering over the panel for extended periods.
[*]I have tried right clicking on empty space in other panels and seeing if I can get into preferences for the left panel that way.
[*]I have tried looking through all of the settings type applications in the System menu.
[*]I have tried restarting X.
[*]I have tried (with much less hope than the rest of the things I attempted.) restarting the computer.
[*]I have read the man page for gnome-panel, which redirected me to the page for gnome-options, which redirected me to the page for gtk-options.
[*]I have read quickly through the GNOME help included with Ubuntu 9.10.
[*]I have searched Google with five different syntactic variations of my problem, and delved three pages through the results for each.
[*]I have looked through Launchpad for a bug that looked like my problem.
[*]I have asked repeatedly (although tried to not be annoying) on irc.
[/LIST]
=================================
Last resort I am trying to avoid:
=================================
Creating a new user would probably fix the problem.

===================
What I'm doing now:
===================
Asking on the Ubuntu forums for help in removing the rogue panel.

====================================
Solution:  (Provided by kelvin.illa)
====================================
[LIST=1]
[*]Open terminal.
[*]Type "gconf-editor"; a window will pop-up.
[*]From the folders on the left, go to / > apps > panels > *
[*]* depends on your panel configuration. The settings for the panel you want to configure should be below to "global" folder within the "panel" folder.
[*]When you have the panel you want to configure selected, uncheck a box on the right that writes "auto_hide"
[/LIST]

---

### Post by kelvin.illa on 2009-11-09
- Open terminal. 
- Type "gconf-editor"; a window will pop-up. 
- From the folders on the left, go to **/** > **apps** > **panels** > *****
 * depends on your panel configuration. The settings for the panel you want to configure should be below to "global" folder within the "panel" folder.
- When you have the panel you want to configure selected, uncheck a box on the right that writes "auto_hide"

This is the reason why I'm not using auto-hide. I want to but I couldn't.

---

### Post by Veovis Muad'dib on 2009-11-10
Thank you very much! That worked.

Autohide works on the top and bottom, but not the sides for me.  Oh well.

---

### Post by kelvin.illa on 2009-11-11
glad to help

---

### Post by rballard on 2009-11-14
if you follow the same advice to get to the gconf panel options but set auto_hide_size to a larger size (i had the same problem and mine is set to 10 now and it works) it may help your expand option work.

---

### Post by Veovis Muad'dib on 2009-11-15
The smallest number I can use is 5.  What about you?

Thank you for this solution, although my current theme now looks bad with left and right panels, so I'm afraid I won't be using this for now.  But the solution is here for anyone else who wants to use it.

---

### Post by User Abuser on 2010-10-11
if there's a menu bar on a stuck panel, you can simply press ALT+F1
Was nice to know that this bug is still in 10.10 :)

---

### Post by kucerarichard on 2011-01-04
Thank you for solution...

Here's a tip:  don't sudo for gconf-edit,  or you will get the root gconf,  and you won't find your autohide setting.

just gconf-edit as yourself.


I ended up deleting the panel anyway and switching entirely to Cairo Dock... (man it's slow,  but whatever)

---

