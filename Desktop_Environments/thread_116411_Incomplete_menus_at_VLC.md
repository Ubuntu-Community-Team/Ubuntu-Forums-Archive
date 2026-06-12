---
title: "Incomplete menus at VLC"
date: 2006-01-12
forum: Desktop Environments
---

### Post by petehall on 2006-01-12
Something that has been bugging me since I upgraded to 5.10 - the version of VLC from universe (0.8.4) seems to have missing menu options. For example, when I was using 5.04 the View menu used to contain the "Playlist" option and a few others, but now it just seems to contain four separators. Similarly the File menu just contains "Open Directory", "Open Capture Device" and "Exit", and a huge pile of separators.

Has this been encountered by anybody else?

Thanks,

Pete

---

### Post by A-star on 2006-01-17
Saeme problem here, no idea what's causing this and I have no clue how to solve it.

---

### Post by petehall on 2006-01-29
[QUOTE=A-star]Saeme problem here, no idea what's causing this and I have no clue how to solve it.[/QUOTE]

I've found a bit of a workaround - I've added the following line to my sources.list:

deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sid main

Then I used synaptic to force 0.7.0 as the installed version. The downside with this is that when I run apt-get from the command line, it tries to upgrade back to 0.8.4. I've been getting around this by using the graphical Update Manager instead, which allows you to uncheck individual packages.

---

