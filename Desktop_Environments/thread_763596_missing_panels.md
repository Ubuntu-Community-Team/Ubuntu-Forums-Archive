---
title: "missing panels"
date: 2008-04-23
forum: Desktop Environments
---

### Post by nicoatridge on 2008-04-23
I've not found any postings with this specific problem. I did a clean install of Hardy Heron Beta and all went well until I added a few more programs, and the add/remove dialog box hung. I rebooted and Gnome came up repeatedly with "OAFID:GNOME_panel_trashapplet" errors - they just flashed on the screen and didn't ask to be acknowledged. I was then left with the very cool default Hardy Heron wallpaper, but no icons or panels - although some desktop shortcuts work, like F12 for desktop search. I've used apt-get to remove and install gnome-applets and ubuntu-desktop, but no joy.

Is anyone else familiar with this problem? If not I'll do some more experimentation and see if I can post a fix.

---

### Post by TCSnyder on 2008-08-25
go into your terminal and try 

gnome-panel

on my machine it says "Gnome panel is already running" so give it a try

---

### Post by Dojan5 on 2008-08-26
First I suggest that you start the terminal.
Run ```
killall gnome-panel 
```then run ```
gnome-panel 
```and it should be back

---

