---
title: "Session startup apps GNOME vs XGL"
date: 2006-07-27
forum: Desktop Environments
---

### Post by benjaminwr on 2006-07-27
Hi,

I am having a problem with my startcompiz script when I load a normal GNOME sesison.

I have added the script into *System - Preferences - Sessions - Startup Programs* to automate the process when I load up XGL but when I go into GNOME it crashes my session.

I know this is what I should expect it to do, but I was wondering if there is anywhere I can add my startcompiz script (other than Startup Programs) that is session independent.

This is what startcompiz does

[I]killall gnome-window-decorator 
wait
gnome-window-decorator & DISPLAY=:1
compiz --replace gconf
[/I]

Cheers

---

