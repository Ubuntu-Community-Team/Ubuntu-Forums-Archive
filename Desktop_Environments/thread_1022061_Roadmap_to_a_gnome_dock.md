---
title: "Roadmap to a gnome dock"
date: 2008-12-26
forum: Desktop Environments
---

### Post by aeosynth on 2008-12-26
I'm not sure whether I should post this here, on brainstorm, or somewhere else, but I have an idea for creating a gnome-panel dock applet:

The AllTray applet ([http://alltray.sourceforge.net/](http://alltray.sourceforge.net/)) can be used, right now, to provide docking features to the gnome-panel. The only additional features it needs to be considered a 'true' dock are automatic window docking (currently you have to click on each window you want dock), and launcher support (currently it can automatically start and dock specific programs, which is almost the same thing). Providing these features won't make it competitive with AWN or OS X's dock, but gosh darn it, it's a start.

---

### Post by Vadi on 2008-12-26
Looks interesting, thanks for pointing it out.

---

### Post by aeosynth on 2008-12-26
Feature dump:

'Send to tray' should be a context menu item, bypassing the whole 'add an extra button' issue. Should have global default (accessible in applet context menu) and per program setting (accessible in program's title bar context menu).

For people who want two task bars, they'd use default 'don't send to tray', and only the programs they mark would use notifisation, acting like Rhythmbox (minimize to window list, close to notification area). Maybe programs that already send to tray would have this enabled by default, but we would force them to act in this consistent way.

For people who want a true dock, they'd use default 'send to tray', and closing a program would close it, no minimization/notifisation, although launchers would of course remain.

Plugins could be created for icons w/o native systray menus - check mail for email programs, Rhythmbox-style menu for other music players.

***

Someone get around to developing this already! :)

---

