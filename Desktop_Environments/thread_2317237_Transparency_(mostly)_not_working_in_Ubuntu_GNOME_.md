---
title: "Transparency (mostly) not working in Ubuntu GNOME 15.10 Wily"
date: 2016-03-14
forum: Desktop Environments
---

### Post by wxnarwhal on 2016-03-14
Platform: x86_64
Distribution: Ubuntu GNOME 15.10 Wily
DE: GNOME Shell 3.16.4


I recently upgraded from Ubuntu GNOME 14.04 LTS to Ubuntu GNOME 15.10 normal.  I've noticed some issues with transparency that I can't figure out and did not have in 14.04.  I'm assuming this is a compositing issue with Mutter, but I am not familiar with settings like I was with Compiz.


Here's what I first noticed.  Using the extension "Dash to dock" I noticed that the formerly transparent Dash is now opaque over a window (Google Chrome in the screenshot) or over the desktop.  I verified that the extension is still set to 70% opacity and it is not being honored.

[IMG]http://i1168.photobucket.com/albums/r485/wxnarwhal/Ubuntu%20forum/dash_transparency_zpszno1byzp.png[/IMG]


I then checked the extension "Workspaces to dock" and noticed that strangely it will honor the opacity settings over windows, but will not over the desktop.

[IMG]http://i1168.photobucket.com/albums/r485/wxnarwhal/Ubuntu%20forum/workspace_transparency_zps2f02yovu.png[/IMG]


These things were minor UI annoyances until I noticed a problem in Nemo.  When I scroll up or down in the directory tree the top or bottom (screenshot, GTK+ Numix Theme) will I assume it is attempting some overlay to indicate that I have reached the end of frame where I am scrolling.  This is more than an annoyance as I cannot see my directories when this happens.

[IMG]http://i1168.photobucket.com/albums/r485/wxnarwhal/Ubuntu%20forum/nemo_transparancy_zpsdbkcgpfo.png[/IMG]


Thanks in advance for assistance.  I will be happy to include any further information as required.

---

