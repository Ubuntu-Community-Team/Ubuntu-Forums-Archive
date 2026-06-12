---
title: "Two volume sliders in top right corner"
date: 2015-11-28
forum: Desktop Environments
---

### Post by joedasilva123 on 2015-11-28
Just recently a few things messed up on my Xubuntu system. It happened after I tried installing VirtualBox then uninstalled it when it was giving errors. My font settings changed for some reason, and now I have two volume sliders showing up in the top corner when I adjust the volume. They show up when I hover over the sound indicator and scroll up or down. There used to be just one. If I click the sound indicator and drag the volume bar that pops up there, it matches with the bottom two sliders in the top corner. The one on top doesn't change. When I scroll with my mouse over the indicator, both bars in the upper corner move in unison. Any ideas?

Thank you

---

### Post by ajgreeny on 2015-11-28
What shows if you right click in the volume icons?  It should show "Indicator Plugin" with a few other options to click.  Do you have two instances of Indicator Plugin in the panel?  You can check what is in the panel by right clicking in it and choosing **Panel-> Panel Preferences->Items** tab, and the list there may give you other clues.

---

### Post by joedasilva123 on 2015-11-28
I right clicked the volume icon and it does show Indicator Plugin. I checked out the Items tab too in the Panel Preferences and there's only one Indicator Plugin listed. I tried removing it and adding it but the same thing is happening. Pretty strange.

One difference I noticed is that the top volume bar will flash white like it's glowing when the volume is maxed out and I keep scrolling up on the mouse wheel. The volume bar on the bottom doesn't do this. Don't know if that helps at all.

---

### Post by ajgreeny on 2015-11-28
Just another thought:
Go to the xfce4 "settings manager" -> "Sessions & Startup" and see if you have both **Xfsettingsd** and the **XFCE Volume Daemon (Pulseaudio)** enabled as startup applications.  If so deselect the Xfsettingsd and see if that helps after a restart or logout and in again for a new session.

---

### Post by joedasilva123 on 2015-11-29
I found something in the Task Manager called 'xfce4-volumed'. When I terminate that task, the second volume bar goes away. When I restart or log out though, that task gets restarted and the problem returns. How can I stop this service from auto-starting?

Thanks

---

### Post by ajgreeny on 2015-11-30
See my post #4 which explains the reason.
Look for both of those processes/applications in the startup applications list and try deselecting one or other of them.

As I said, I have the **xfce4 volume daemon** enabled but the **xfsettingsd** disabled for autostart..

---

