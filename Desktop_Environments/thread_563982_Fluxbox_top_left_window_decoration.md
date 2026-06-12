---
title: "Fluxbox top left window decoration?"
date: 2007-09-30
forum: Desktop Environments
---

### Post by PurposeOfReason on 2007-09-30
So I'm trying out fluxbox right now and everything is going very smoothly. Everything is just how I want it actually except on the top left of every window decoration, is almost like another one. It has the same title, everything. I've seen screenshots and it's not there, so how do I remove it? 

Thanks.

---

### Post by kerry_s on 2007-09-30
are you talking about the tab? you can go to the settings and have it in the title bar.
tabs are for grouping, try it drop 1 window on another.

---

### Post by PurposeOfReason on 2007-09-30
That's probably it. What setting is this? Sorry for being a fluxbox idiot.

---

### Post by PurposeOfReason on 2007-09-30
Nevermind, I got it.

---

### Post by kerry_s on 2007-09-30
> **PurposeOfReason said:**
> Nevermind, I got it.

do a little reading learn to use the groups it's a great feature in fluxbox.

[http://fluxbox.sourceforge.net/docbook/en/html/book1.html](http://fluxbox.sourceforge.net/docbook/en/html/book1.html)

---

### Post by PurposeOfReason on 2007-09-30
That was a helpful read, thanks. By any chance do you know how to change the cursor theme? I've tried the .Xdefaults way, which worked until the wallpaper loaded.

---

### Post by kerry_s on 2007-10-01
> **PurposeOfReason said:**
> That was a helpful read, thanks. By any chance do you know how to change the cursor theme? I've tried the .Xdefaults way, which worked until the wallpaper loaded.

i usually change the default cursor.

**sudo your-editor /usr/share/icons/default/index.theme**

change

Inherits=core
to
Inherits=your-cursor

that will make your cursor the standard.

there's also a way of using .gtkrc-2.0 to select the cursor, but i can't remember cause i prefer that other way.

just a reminder, you need to log out and back in for cursor changes.

---

### Post by PurposeOfReason on 2007-10-04
This is slightly different, but is it possible to make the window decoration transparent to a degree? I tried changing the theme pixmap but that didn't help; or I just did it wrong.

---

### Post by RedSquirrel on 2007-10-04
The transparency is in your menu. 

Fluxbox menu -> Configure -> Transparency. 

You probably have to restart Fluxbox to see the change. Fluxbox menu -> Restart.

---

### Post by PurposeOfReason on 2007-10-04
That did the full window.

---

### Post by RedSquirrel on 2007-10-04
There is no way to make the transparency apply to individual window decorations. When you apply it, it affects the tab, titlebar, etc.

---

