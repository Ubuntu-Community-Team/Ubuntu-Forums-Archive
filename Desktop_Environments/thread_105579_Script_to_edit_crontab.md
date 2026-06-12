---
title: "Script to edit crontab?"
date: 2005-12-18
forum: Desktop Environments
---

### Post by Cordate on 2005-12-18
[COLOR="DarkSlateGray"][COLOR="DarkGreen"]Ok, so here's what I'm wanting to do:

I have a crontab entry that runs a script at a given interval to change my desktop's wallpaper. Sometimes I'm getting one that I like a lot and I'd like to have a quick way to turn off the scheduled running of the script so that I can enjoy the wallpaper longer. 

It seems like maybe I could write a script that would swap out a file (via renaming or moving) to replace my crontab with one that doesn't have the wallpaper script job in it. But it looks like the crontab file isn't accessible like a regular file. One page on crontab that I found says "[COLOR="Purple"]The crontab files are not edited (or created) directly and you do not have access to the file without invoking it from the crontab command.[/COLOR]" So..... any ideas on how I can achieve my on/off script switch? Opening a terminal and editing the cron entry every time is awfully clunky.

Thanks!

-Cordate[/COLOR][/COLOR]

---

### Post by schilcha on 2005-12-18
Quick and dirty suggestion:

To your existing script add the following if-condition:
if a certain file exists (e.g. $HOME/.keepwallpaper), then do not change the wallpaper; else change the wallpaper. You create this file through e.g. touch $HOME/.keepwallpaper and rm it easily (even through an application launcher in a gnome panel)

---

### Post by Cordate on 2005-12-18
[COLOR="DarkGreen"]That sounds like it would do just fine- I'll give it a shot.

I can make a little script to create the file if it doesn't exist, and delete it if it does, and assign it to a button, then I have a toggle switch. Thanks!

Edit: This is fun! Now the scripts all work ok (I even got to learn a bit of Python to make the wallpaper script do the checking for the toggle file) but now I'd like to have some visual indicator as to the state of the switch. I'd like the appearance of the panel lancher for the toggle script to change so I know when it's on or off. 

I've made the script change swap 2 files for the icon, but it looks like the panel doesn't update the change. Does Gnome store its icon info separately somewhere, and/or is there a way to alter this with my script? (I could run "killall gnome-panel", but it's not the smoothest transition :) )

Alternatively, is there another way I might get a visual indicator like this? [/COLOR]

---

### Post by schilcha on 2005-12-19
Huh, I've to admit that I cannot contribute a single bit to this :-(

---

