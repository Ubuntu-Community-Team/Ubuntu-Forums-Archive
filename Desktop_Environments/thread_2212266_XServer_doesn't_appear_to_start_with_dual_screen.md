---
title: "XServer doesn't appear to start with dual screen"
date: 2014-03-20
forum: Desktop Environments
---

### Post by jeff46 on 2014-03-20
Hi, long time reader, first time poster, so please point me in the right direction if I've posted in the wrong place or more info is needed.

I have a brand new Dell Precision M3800 (normal display, not the ridiculously high res one) on which I installed Ubuntu 12.04 and installed the latest NVidia drivers (331, but I've also tried 319). I have an external monitor connected through the displayport out, which appears to work fine, except for logging in or restarting X server (ctrl+alt+backspace). If I try to do so, some console text comes up shortly on the internal monitor, then the same text appears shortly on the external monitor, then both monitors flicker a bit (sequentially) and ultimately, the login screen shows. This is the most important issue to solve for me, because of how annoying it is to disconnect my monitor every time I login.

FYI: the graphics card is a Quadro K1100M, as well as an integrated intel device.

Additionaly, the nvidia-settings tool shows one lumped screen, rather than two as the 'Displays' utility shows (see picture).
[ATTACH=CONFIG]251316[/ATTACH]

This is similar to how the worspaces are arranged, switching workspaces switches content on both monitors, which is annoying (let alone disconnecting my external monitor when I go on the move). Ultimately, I'd like to maintain the 9 workspaces in a grid and show one workspace on each monitor, but first things first I guess :)

---

