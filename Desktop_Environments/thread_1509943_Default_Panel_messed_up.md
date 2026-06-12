---
title: "Default Panel messed up"
date: 2010-06-14
forum: Desktop Environments
---

### Post by needhelppeeps on 2010-06-14
Hey all,

The default top panel keeps getting messed up. Sometimes it comes up without the power symbol logout applet and the sound applet.

I found a partial solutions, which is to run the following script.


#!/bin/bash
gconftool-2 --recursive-unset /apps/panel
pkill gnome-panel

but is there a better way? I am running 10.04

---

