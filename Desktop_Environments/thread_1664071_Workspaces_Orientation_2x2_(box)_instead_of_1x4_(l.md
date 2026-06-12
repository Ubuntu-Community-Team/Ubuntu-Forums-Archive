---
title: "Workspaces Orientation: 2x2 (box) instead of 1x4 (line)"
date: 2011-01-10
forum: Desktop Environments
---

### Post by the_weekend on 2011-01-10
I've spent a number of hours trying to figure out how to fix this. In normal gnome desktop the default was (is) for 4 workspaces to show up in a line. I want that in unity.

I've tried using gconftool-2, but can't find a simple list of metacity settings. Settings like "#define _NET_WM_ORIENTATION_VERT 1" seemed promising but doesn't seem to be a usable variable.

HELP!

---

### Post by TechWiz2100 on 2011-01-10
Just right click on the workspaces panel and click properties for a little box with rows and columns.

---

### Post by the_weekend on 2011-01-10
Do you mean the button (for me it's purple( that shows you all the workspaces? There's no "workspace panel" in Unity, just that button. When I right click it, it says "workspaces", which I can't click. If I click the button, it shows me all my workspaces tiled across the screen.

---

### Post by TechWiz2100 on 2011-01-10
Unity is based off Gnome so you might be able to add panels to your menu bar. Add workspace switcher then right click on that. If you can't add panels then I dunno what to do from there but I hope panels stay because they are a very useful tool and I hear 11.04 is using Unity as default...

---

### Post by the_weekend on 2011-01-25
Bumping this thread because I really would like to fix this.

---

### Post by matthew.mattoon on 2011-05-20
In case someone has not figured this out...  If you are using Unity on 11.04 and would rather have your 4 workspaces in a line (rather than the 2x2 box by default) you can adjust this easily.

# apt-get install compizconfig-settings-manager

Then launch compizconfig-settings-manager

Under General Section

General Options

Desktop Size tab

Horizontal Virtual Size and Vertical Virtual Size can be adjusted for desired effect.

Default in 11.04 is H2 V2.  For similar setup to pre-Unity use H4 V1.

This does not disable any of the new Unity features.

-matt

---

