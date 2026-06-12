---
title: "Peculiar Gnome window and keyboard issue"
date: 2010-09-11
forum: Desktop Environments
---

### Post by Shufei on 2010-09-11
Hello dears, Rank greenhorn newbie here; please be gentle.  ;)

I updated my vanilla Karmic Koala, installed on a 5 year old toshiba laptop with winxp dual boot, to Lucid Lynx yesterday, using the gui updater.  Upon restart of the system, all seems well up to login.  Once I log in to my user account, I find the following odd issues:

1. Windows do not have a top-bar and seem "glued" to the top of the screen.  I can not move nor resize windows.  There are no "close" or "minimize", etc. buttons.  (I know that Lynx moves these to the left, mac style, but they simply aren't there at all.

2. The window selector on my bottom bar does not show any apps or windows.  I've tried reloading the widget to no avail.

3. I can not type in windowed text.  This includes terminal!  Looking through search, I found the suggestion to reload or reinstall metacity, but without a terminal I'm at a loss how to do that as suggested.  I can type into the login screen  fine, but once in the gui the windows don't accept text.

-Bootup seems fine.  No error messages.  Winxp loads fine from GRUB.  QED.
-I can use a mouse.  When I load a program from the dropdown menus, it loads fine save these errors.  I can manipulate by mouse most options.  Just can't type in Gnome.
-Dropdown menus inside each program seem to work fine.

Forgive my palpable newbiness.  Any advice would be greatly appreciated.

Shufei

---

### Post by chopinhauer on 2010-09-11
Reloading **metacity** when no Windows Manager is running can be hard. Nevertheless you can switch to a text terminal with CTRL+ALT+F1, log in, type
```
DISPLAY=:0 metacity --replace
```and switch to the X server again with CTRL+ALT+F7.

---

### Post by Shufei on 2010-09-11
Thank you dearly, chopinhauer.  I figured it would be something easy like this.  Reloading metacity indeed did the trick.  (Next time, with Mumbly Moose or whatever, I'm going for a clean install!)

Thanks again!

---

