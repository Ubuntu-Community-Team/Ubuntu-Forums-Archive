---
title: "openChrome + Wine"
date: 2007-07-22
forum: Gaming &amp; Leisure
---

### Post by themerion on 2007-07-22
It seems like most wine-run games simply won't work with the VIA openCHROME drivers.

This page: [http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Compiling+the+source+code+on+Gentoo](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Compiling+the+source+code+on+Gentoo)  provides a solution for Gentoo users, but also state that the problem does not exist in Mesa 7.0 (which was released on June 22th).

So, it seems to me that upgrading to the latest version of Mesa would solve the problem. ( I've not been able to test this myself though, as I'm still trying to figure out how to make apt or synaptic let me install Gutsty packages... )

Can anyone verify/disprove this?

---

### Post by MarkusRTK on 2007-07-28
I'm having the same problem; Wine either crashes or has no graphics (white screen usually) on almost any Windows application save terminal-based text games. My suspicion is that Mesa 7.0.0 might fix that (as well as a number of other bugs with OpenChrome support) because it adds OpenGL 2.0 and 2.1 support. You never know obviously.

Haven't been able to find an official backport of Mesa 7.0 to Feisty, but trolling Google I came across some unofficial test packages here -- [http://tormod.freeshell.org/linux/mesa/](http://tormod.freeshell.org/linux/mesa/) -- no idea who made them or what the story is. I'm going to try them, see if my laptop doesn't catch fire, and let you know if it helps.

Meanwhile, anybody know of other efforts to backport Mesa 7.0 to Feisty, or any other new developments in dealing with UniChrome/OpenChrome?

---

### Post by MarkusRTK on 2007-07-28
Nope, no dice -- in fact this version of Mesa (bearing in mind it's an unofficial backport) caused some crazy lockups when it tried to play with Wine. Looks like I'll just be waiting.

---

