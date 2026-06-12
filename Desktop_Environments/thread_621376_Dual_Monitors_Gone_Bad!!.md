---
title: "Dual Monitors Gone Bad!!"
date: 2007-11-23
forum: Desktop Environments
---

### Post by frickea86 on 2007-11-23
I was just messing around with the settings in "screen and graphics preferences" menu and I enabled screen 2.  and logged out, well now all i get is the command prompt.  No gui, and I get an error

> GDM cannot start, gdm.conf must be configured correctly.

Thats, it nothing else, i get a command prompt, login and can do anything threw the prompt but nothing with graphics.

HELP!!...:confused:...its probably something dumb and i'm just being a noob

---

### Post by sirdilznik on 2007-11-24
> **frickea86 said:**
> I was just messing around with the settings in "screen and graphics preferences" menu and I enabled screen 2.  and logged out, well now all i get is the command prompt.  No gui, and I get an error



Thats, it nothing else, i get a command prompt, login and can do anything threw the prompt but nothing with graphics.

HELP!!...:confused:...its probably something dumb and i'm just being a noob

I don't have much experience with a dual monitor setup, but I imagine that when you enabled that option it may have altered something in your /etc/X11/xorg.conf.  Could you post the contents of that file, particularly the graphics, server, and monitor sections?

---

