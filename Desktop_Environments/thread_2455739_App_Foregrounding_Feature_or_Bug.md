---
title: "App Foregrounding Feature or Bug?"
date: 2020-12-26
forum: Desktop Environments
---

### Post by jeevans01 on 2020-12-26
Some apps in Ubuntu, such as MuseScore and the Trash, do not foreground new windows and dialogue boxes in a way that I would expect. The "Save As" window in MuseScore is brought up behind the active window and Ubuntu delivers a notification saying that it "is ready" through something called "Portal." The Trash opens it's "are you sure you want to delete..." dialogue behind the active window as well. Is this a feature in Ubuntu to prevent disruption to work in the active window, is it a bug, or am I missing something?

A few details:
Ubuntu 20.10
Gnome 3.38.1
X11
MuseScore installed as FlatPak.

---

### Post by TheFu on 2020-12-26
Window placement is controlled by the window manager. It is only controlled by the app to the level that the placement of the opening window can be influenced by asking the WM to make that part of the new window creation properties. That is all.

For a solution, I'd look at the WM settings for window behavior.

I don't use gnome3 so don't know how they've mucked the wm up or whether the DE is doing something funky. Looks like some gnome extensions interfere sometimes. sorry.

---

