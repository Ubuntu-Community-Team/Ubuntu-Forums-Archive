---
title: "Relative brightness of desktop icons"
date: 2012-08-26
forum: Desktop Environments
---

### Post by vasa1 on 2012-08-26
Xfce 4.10 on Ubuntu 12.04.

I'd like some help understanding what's going on here.

The leftmost image is a bit of my desktop with **no icon single-clicked**.
The *Home* folder and the *MyDesk* icons are of equal brightness.

The middle image is after I **single-click on the *Home* folder**. The icon darkens whereas the text brightens, both relative to when no icon is clicked. The text brightening is intended but I don't want the icon to darken. Is there a way to stop the icon from darkening? The *Home* folder icon is noticeably darker than the *MyDesk* folder icon.

I can get the Home folder icon, or any other icon to brighten (when it isn't single-clicked) by just hovering the mouse cursor over it or its text (rightmost image).

To summarize, I don't want icons to darken when I single-click on them. The icon text brightening is enough to indicate which icon is selected.

---

### Post by vasa1 on 2012-08-26
When I try the Ambiance and Radiance themes, single-clicking an icon on the desktop causes the icon to acquire an orangish hue.

After some more poking around, it appears that both the icon and the icon text get the same hue and that the hue is dependent on "selected_bg_color". Hmmm ...

---

