---
title: "Ubuntu Netbook Remix: gnome-panel and nautilus don't appear"
date: 2010-02-01
forum: Desktop Environments
---

### Post by baichi9992 on 2010-02-01
Hi,

I recently [installed]("http://aionlevelbot.net/Hack/html/list1-1.html") Ubuntu Netbook Remix (UNR) on my Asus Eee PC.
at first it worked well, expect for wireless, but after some configuration it worked.

After I updated however, when I restarted the panel and window managers didn't work: there was a semi-black bar on top and when I started something with the launcher it had not borders and couldn't be moved.

When I switched back and forth to classic and again to netbook mode everything worked perfectly.

It also works fine if I type the following two commands into the terminal:

Code:
(gnome-panel &)(metacity &)
which are designed to run (and do run) gnome-panel and metacity seperate from the console.

My question is: how do I fix this so I don't have to do that all the time?

I have also made a bash script which will do it every reboot, but [I]("http://aionlevelbot.net/") find that a rather ugly solution.


Code:
#!/bin/sh# These dissapear, I'm trying to restore them# Check if a nautilus process existsif [ `pgrep -c metacity` = 0 ]; then		(nautilus &) # Start nautilusfi# Check if a gnome-panel process existsif [ `pgrep -c gnome-panel` = 0 ]; then	(gnome-panel &) # Start gnome-panelfi

---

