---
title: "Position of Gnome Context Menu"
date: 2015-10-23
forum: Desktop Environments
---

### Post by stefanadelbert on 2015-10-23
I recently installed Ubuntu 15.10 (Beta 2) on my Dell XPS laptop and ran it in native resolution (3200x1800). I then installed [FONT=Courier New]i3[/FONT] and noticed that Gnome context menus (e.g. right-clicking [FONT=Courier New]nm-applet[/FONT] in the systray, right-clicking [FONT=Courier New]gnome-terminal[/FONT], right-clicking [FONT=Courier New]nautilus[/FONT]) had their positions constrained to the top-left quadrant of the display. If I right-click near the top-left of the display then the context menu is in the correct position. But if I click anywhere below or to the right of the centre of the display then the context menu is positioned above and to the left of the centre of the screen.

[ATTACH=CONFIG]265137[/ATTACH]

I've attached a screenshot showing the context menu for [FONT=Courier New]nm-applet[/FONT] after right-clicking on its icon (bottom right). I noticed after I had taken the screenshot that the cursor *appears* to be at the bottom-right of the context menu (maybe this is a clue). Certainly that's not where the cursor was when the right-clicking happened.

I've played with [FONT=Courier New]scale-factor[/FONT] (com.ubuntu.user-interface) and I switched resolution down to 1920x1080, but the effect was the same. [FONT=Courier New]notify-osd[/FONT] notifications had the same problem.

**Does anyone know what controls the position constraints for gnome applications? What could I do to correct this?**

---

