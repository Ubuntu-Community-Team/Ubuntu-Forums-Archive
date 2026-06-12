---
title: "Keyboard Shortcuts with Win key"
date: 2005-12-23
forum: Desktop Environments
---

### Post by sdr_ar on 2005-12-23
Hi, I was trying to create a shortcut to access K Menu by only pressing the Win key, but KDE 3.5 only lets me use it in combination with another key. Is there any way to create a shorcut like this?

---

### Post by rjwood on 2005-12-23
[quote=sdr_ar]Hi, I was trying to create a shortcut to access K Menu by only pressing the Win key, but KDE 3.5 only lets me use it in combination with another key. Is there any way to create a shorcut like this?[/quote]

I was able to do it in gnome--not sure about kde

---

### Post by grendel_khan on 2005-12-23
I assume you're talking about configuring with **kcmshell keys**. Perhaps this should be considered a bug in that. Apparently, this was [the default kde behavior](http://bugs.kde.org/show_bug.cgi?id=84222), but was dropped last year due to requiring hacks in the X server.

It's keycode 115, if you have a chance to enter it that way. (That's the keycode that X sees.) If you mapped it to run the command **dcop kicker kicker ShowKMenu**, that'd work. Meantime, there's a KDE wishlist bug ([118919](http://bugs.kde.org/show_bug.cgi?id=118919)) about it.

---

### Post by obibok on 2005-12-26
[QUOTE=sdr_ar]Hi, I was trying to create a shortcut to access K Menu by only pressing the Win key, but KDE 3.5 only lets me use it in combination with another key. Is there any way to create a shorcut like this?[/QUOTE]
KDE Control Center->Regional & Accessibility->Xkb Options

[X] Enable xkb options
- Third level choosers
* Press any of the Win-keys to choose 3rd level

KDE Control Center->Regional & Accessibility->Keyboard Shortcuts
Shortcut Schemes->Global Shortcuts

- Panel
* Popup Launch Menu

Shortcut for Selected Action

(O) Custom

[Advanced]

(O) Alternate shortcut

- press the Win-key (ISO_Level3_Shift)

This and many more tweaks can be found at [http://linuxtuneup.blogspot.com/](http://linuxtuneup.blogspot.com/)

---

### Post by sdr_ar on 2006-03-31
What I get applying this is that I can open the menu with Alt Gr, not with the WinKey.

---

