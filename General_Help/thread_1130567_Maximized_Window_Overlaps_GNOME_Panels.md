---
title: "Maximized Window Overlaps GNOME Panels"
date: 2009-04-19
forum: General Help
---

### Post by andrewk8 on 2009-04-19
I am running Ubuntu 8.10 with Compiz (desktop cube).  When I used CTRL+ALT+Left Arrow to move from workspace #2 to workspace #1, the Firefox browser that was maximized in workspace #1 started overlapping the GNOME panels and the window title bar (with the minimize / maximize / close buttons) is missing.  (See attached.)

I flipped back to workspace #2 and opened up something else (GIMP) and its palette and layer window borders are missing, too.

I used the System Monitor to kill Firefox, then re-start Firefox and that didn't work.

I changed from Compiz to Metacity and it didn't bring back my window title.

So:
[LIST]
[*]All my windows overlap the GNOME panels.  I can't open a new application unless I switch to a new workspace
[*]The window title bar is missing
[*]I can't minimize, un-maximize or move the windows because there is no window title
[/LIST]

---

### Post by killerdogg77 on 2009-04-20
You can hit f11 to change from full screen.Try unchecking Legacy fullsreen support in the workaround optins in compiz manager.

---

### Post by andrewk8 on 2009-04-20
"F11" sort of worked.  Pressing F11 once put Firefox INTO full screen mode.  Pressing F11 a second time took Firefox out of full screen mode and restored the window title and minimize / maximize / close buttons.

Attached is a screen shot with Firefox in full screen mode.  Note that even in full screen mode, Firefox includes minimize / maximize / close buttons.  In my original screen shot, Firefox didn't have any - they were still in the window title, which was missing.

So even though Firefox occupied the full screen, including covering up the GNOME panels, it wasn't technically in full screen  mode.  I had to put it INTO full screen mode then get it out of full screen mode to restore the window borders.

Bug?  (Yes?)  Compiz?  GTK Window Decorator?  GNOME?

---

### Post by killerdogg77 on 2009-04-20
Try looking here[http://ubuntuforums.org/showthread.php?t=963286&highlight=firefox+fullscreen](http://ubuntuforums.org/showthread.php?t=963286&highlight=firefox+fullscreen)
or here
[http://ubuntuforums.org/showthread.php?t=810804&highlight=firefox+fullscreen](http://ubuntuforums.org/showthread.php?t=810804&highlight=firefox+fullscreen)

---

