---
title: "Is there a good desktop zoom feature for Ubuntu 18.04?"
date: 2020-02-25
forum: Desktop Environments
---

### Post by davy jones on 2020-02-25
I just upgraded to 18.04 from 14.04. In 14.04, I had Compiz that had a really useful desktop zoom feature that let you zoom as much or as little as you wanted. I've read online that Compiz is incompatible with Gnome and only works with Unity and that's why it can't work on 18.04. But in 14.04, I was actually using Gnome and not Unity and it was still working. I tried installing Compiz-core and Compiz-plugins as well as CCSM in 18.04 but it doesn't work. I have to manually start Compiz in the terminal and the core plugin fails to start. On top of that, the toolbar for all my windows vanishes when I do this. Compiz's zoom feature starts working, but when I stop running the command my whole desktop hangs.

I'm not hung up on Compiz but 18.04's universal access zoom feature is not helpful at all. It magnifies the screen by a minimum factor of 2, which is too much for me. Is there any way to be able to zoom the desktop in 18.04?

---

### Post by CatKiller on 2020-02-25
> **davy jones said:**
> But in 14.04, I was actually using Gnome and not Unity and it was still working.

Compiz - a window manager - worked OK as a drop-in replacement for Metacity, Gnome's old window manager. It doesn't work so well as a drop-in for Mutter, Gnome's new window manager, since that's picked up a whole load of Wayland stuff.

> I have to manually start Compiz in the terminal and the core plugin fails to start. On top of that, the toolbar for all my windows vanishes when I do this. Compiz's zoom feature starts working, but when I stop running the command my whole desktop hangs.

When you close the terminal window, and end the compiz process, you no longer have a window manager working. If compiz works at all in your environment, ```
compiz --replace &
``` *should* allow you to close the window without ending the compiz process. Otherwise, running it from whatever Gnome's Run dialogue is will do the same thing. You'll also need to start a window decorator: Gnome's is all tied up with Mutter and Wayland now, so you'll need to start one that will work with Compiz. Of course, the window decorators that work with Compiz are sometimes a bit finicky.

> I'm not hung up on Compiz but 18.04's universal access zoom feature is not helpful at all. It magnifies the screen by a minimum factor of 2, which is too much for me. Is there any way to be able to zoom the desktop in 18.04?

To be honest, you'll likely be a lot happier with KDE than Gnome. The Gnome devs really don't want Gnome users to have configurable options - at all - and their choices are downright odd. Coming from Compiz that approach is particularly jarring. KDE has a lot of the same options (although not all - I miss mipmapping of the thumbnails) as Compiz, including the desktop cube and both a magnifier and a zoom.

---

### Post by deadflowr on 2020-02-25
Gnome has built in zoom feature, probably turned off.
try
alt +super +8 to enable 
zoom in is alt + super +=
zoom out is alt + super + -
My issue is it jumps too far, like if normal is 100% then one click more than doubles it, perhaps it jumps to 300%.
Or a least it feels that way.

Edit: I guess it does only jumps 100% per zoom click,
(Normal being 100%, one click equals 200% second click to 300%, and so on)
though I wish it would be adjustable to only go something like 50% per click.

---

