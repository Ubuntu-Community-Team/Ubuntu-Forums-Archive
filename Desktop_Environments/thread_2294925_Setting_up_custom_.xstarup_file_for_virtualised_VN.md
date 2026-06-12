---
title: "Setting up custom .xstarup file for virtualised VNC session"
date: 2015-09-14
forum: Desktop Environments
---

### Post by amnation545 on 2015-09-14
Hi All,

I've been VNC to create virtual desktops on 14.04LTS  and Unity (or really any GTK3-based) desktop doesn't play nicely and doesn't render a usable desktop.

I've been able to get things working just fine with KDE-Plasma and XFCE but I want to get it running with MATE if possible as I know it's still running GTK2.

I've been creating a script to tell the software to render different desktops but can't figure out what to put to get MATE working.

For example, with XFCE, I'd enter:

[TABLE="width: 500"]
[TR]
[TD]#!/bin/sh
DESKTOP_SESSION=xfce
export DESKTOP_SESSION
startxfce4
vncserver-virtual -kill $DISPLAY[/TD]
[/TR]
[/TABLE]


Any recommendations for getting MATE to play nicely appreciated.  I've already tried several permutations of lines 2 and 4 but without success.

Any suggestions?

---

