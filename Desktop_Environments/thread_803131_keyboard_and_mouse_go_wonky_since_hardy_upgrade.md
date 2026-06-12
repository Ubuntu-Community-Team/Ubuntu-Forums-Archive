---
title: "keyboard and mouse go wonky since hardy upgrade"
date: 2008-05-22
forum: Desktop Environments
---

### Post by akahige on 2008-05-22
Since upgrading to Hardy, I've noticed a random problem that I cannot get a handle on: every so often, the keyboard or mouse just wig out. The mouse pointer will disappear and there will be no control. The problem of the moment is that the keyboard has ceased to respond to the caps or num locks (the keyboard indicator lights don't respond).

I'm actually typing this in VMware because for some reason, *it* will allow me to type capitals, whereas the Linux desktop won't (and pasting it over to the Linux Firefox). @%@$!!

Unlike problems where people report freezes, crashes, or hangs, I'm not getting any of that. Just this keyboard or mouse behavior. I don't know what triggers it, and I don't know how to diagnose or fix it. Things usually work themselves out if I beat on enough keys, but that's hardly scientific or reliable.

EDIT: My suspicion is that something is remapping the keyboard. I just tried dragging and dropping a file on the desktop into a folder on the desktop. In order to move the file (vs. copying it), you have to hold the shift key down. As soon as I hit shift, everything on the desktop disappeared as XFCE decided that it didn't want to manage the desktop any longer. (Everything came back when I dug through the config pane, but this keyboard thing is freaky.)

I'm not running any kind of display compositing (which seems to be the cause of some people's problems).

I'm hoping someone has some ideas...



The system is: Hardy on AMD 64, Xubuntu, dual monitors.

---

