---
title: "Xscreensaver kills beryl"
date: 2007-01-22
forum: Desktop Environments
---

### Post by rabid emu on 2007-01-22
Ok so since the update to 0.1.99.2 beryl as been running fine, except when the screensaver comes on or when I lock the screen.  I've replaced gnome-screensaver with xscreensaver a while ago and never had problems, but now when it comes out of screensaver (or lock) when I'm using Beryl/xgl it goes to a black screen and I have to go to a virtual terminal and kill xorg to get a desktop back.  Any idea what's wrong or how to fix it?

---

### Post by rabid emu on 2007-01-22
Update.  At the aforementioned black screen, I found that the desktop still exists, kind of.  If I move the mouse around I can see the tool tips pop up for varying taskbar items.  Because of this, if I can randomely locate the beryl-manager icon, I can click it and tell it to reload the window manager, and all is well.

It's not a pleasant solution so now I'm wondering if there's a way in gnome, with beryl running on top of it, to bind a key such as Alt + R, to reload beryl.  The command is beryl --replace.

---

