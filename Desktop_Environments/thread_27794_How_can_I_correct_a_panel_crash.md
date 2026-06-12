---
title: "How can I correct a panel crash ?"
date: 2005-04-17
forum: Desktop Environments
---

### Post by mokum on 2005-04-17
Hi,

While adding a drawer to the gnome panel, I got a message "Error, expected list value" (or something similar). Since then the colors of my gnome2 apps (like the panel) are gone, I no longer have a panel menu (Apps, Places, System) and the drawers are gone.

Gnome1 apps (or should I say gtk1 apps) like sylpheed-claws work fine, but gnome2 apps lack colors (e.g. backgrounds are black mostly). Probably some settings 'just' got garbled, but which one and how to correct them ? Is this the equivalent of those horrid windows registry problems ?

What can I do to correct this without doing something drastic like starting all over ? 


Et

---

### Post by TravisNewman on 2005-04-17
You definitely don't need to start over ;)

One thing you can do is login from the CLI (ctrl+alt+f1) and delete any gnome settings from your profile. That's time consuming, but it's better than reinstalling ubuntu altogether.

Before you start, you should create another user and log in with it, to see if the problem is system-wide or if it's just with your profile.

---

### Post by mokum on 2005-04-17
[QUOTE=panickedthumb]You definitely don't need to start over ;)

One thing you can do is login from the CLI (ctrl+alt+f1) and delete any gnome settings from your profile. That's time consuming, but it's better than reinstalling ubuntu altogether.

Before you start, you should create another user and log in with it, to see if the problem is system-wide or if it's just with your profile.[/QUOTE]

I've allready done that. The 'guest' account doesn't have these problems, so it's limited to one user. And I did try to change some settings while in a console. But which one should I change ? That's the $64k question. I tried to find files with references to for instance the drawers, but couldn't find any.

---

### Post by mokum on 2005-04-18
Problem solved, cog (Gnome advanced configurator) appended a few includes in my .gtkrc-2.0 rc file. One of the included files had an erroneous line. After removal of the includes I got my colors back.

The disappearing of my drawers seems to be a different problem. But since I had to rearrange my drawers and launchers anyway, no real harm done. Reading up on Gnome is not a bad idea though ;o).

Et

---

