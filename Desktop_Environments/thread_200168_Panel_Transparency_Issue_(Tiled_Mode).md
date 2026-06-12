---
title: "Panel Transparency Issue (Tiled Mode)"
date: 2006-06-19
forum: Desktop Environments
---

### Post by pRedat0r on 2006-06-19
Hi,

I am having issues with setting transparency on a gnome panel, when the wallpaper is set to tiled.  All other modes for wallpaper seem to work just fine, but when I set it on tiled, then the transparent area has a strange hue, depending on the wallpaper used.  For instance, if the wallpaper is blue, then the transparent area is brown, if the wallpaper is greenish, then the area is yellow, etc.

Does anyone else have this issue?

I have the newest fglrx driver from the repos, but im not sure if this is related to that, or just the gnome panels themselves.  I might give VESA mode a try to determine that, but i'm not going to run that all the time, so hopefully someone knows how to fix this, or if it is related to the driver, or gnome itself.

By the way, I am NOT running XGL, just the stock Xorg.

Attached is a screenshot to show you what I mean -- see the bottom panel.

Thanks!

---

### Post by vyruss on 2006-06-19
[QUOTE=pRedat0r]I am having issues with setting transparency on a gnome panel, when the wallpaper is set to tiled.  All other modes for wallpaper seem to work just fine, but when I set it on tiled, then the transparent area has a strange hue, depending on the wallpaper used.  For instance, if the wallpaper is blue, then the transparent area is brown, if the wallpaper is greenish, then the area is yellow, etc.

Does anyone else have this issue?

I have the newest fglrx driver from the repos, but im not sure if this is related to that, or just the gnome panels themselves.  I might give VESA mode a try to determine that, but i'm not going to run that all the time, so hopefully someone knows how to fix this, or if it is related to the driver, or gnome itself.

By the way, I am NOT running XGL, just the stock Xorg.[/QUOTE]


I cannot replicate this with the latest kernel+fglrx (no xgl). 

Could it be a bug in the theme you are using? 

Why a double screenshot? Are you using dual monitors? Could it be something wrong with xinerama, etc?

---

### Post by pRedat0r on 2006-06-19
I have "big desktop" mode, with 2 monitors.  Dont think it is an issue with the theme, it seems to happen no matter what theme i have applied, even the default human one.  There is one guy in another thread has the same issue with an nvidia board, so im not completely sure that its an fglrx issue.  All i know is this is really annoying!!

---

### Post by vyruss on 2006-06-19
[QUOTE=pRedat0r]I have "big desktop" mode, with 2 monitors.  Dont think it is an issue with the theme, it seems to happen no matter what theme i have applied, even the default human one.  There is one guy in another thread has the same issue with an nvidia board, so im not completely sure that its an fglrx issue.  All i know is this is really annoying!![/QUOTE]

My guess would be it has something to do with your dual desktop. The best you could do is file a bug in Launchpad, so that the developers know about this and can replicate it in order to fix it.

---

### Post by mcduck on 2006-06-20
It's a bug in the latest Gnome panel, already reported and confirmed in Launchpad (and upstream too, if I remember right.)

The same bug occurs when you use a transparent packground picture in your panel.

---

