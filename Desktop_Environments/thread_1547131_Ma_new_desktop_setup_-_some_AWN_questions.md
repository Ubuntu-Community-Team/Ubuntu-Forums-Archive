---
title: "Ma new desktop setup - some AWN questions"
date: 2010-08-06
forum: Desktop Environments
---

### Post by Zorgoth on 2010-08-06
So I've finally gotten rid of my GNOME panel using a combination of Cairo-Dock, AWN, and gnome-do in place of Alt-F2.  The fact that this change happened on my work computer before my home computer confuses me greatly and I have no idea why, since of course at work I am very busy and would never waste time configuring my desktop :D

To get rid of gnome-panel at startup I replaced /usr/bin/gnome-panel with an empty executable text file and backed up the old one.  I attached a screenshot of my new desktop.

I have cairo-dock on the bottom with most of my stuff, and AWN on the left side (not the top because I want to have more vertical screen space).

On AWN I have a clock/calendar, main menu with separate places menu (which I don't use all that much), notification area/daemon, to-do list (I don't normally use that kind of application, but AWN's is really perfectly designed), and awn-system-monitor.

So I have three main problems with my current setup:

1) I would really like AWN to behave like my cairo-dock where it hides only if a window is maximized.  I would also like it to hide when guake drops down.  Otherwise I want to see it, and I want to be able to se eit by hovering my mouse.  Problem is, AWN's "Intellihide" and "Window Dodge" require AWN to have the task manager, and I prefer cairo-dock's task manager.  There is a "Custom" option in AWN - how do I configure it?  Currently I have the suboptimal arrangement of AWN -"always visible" and set to "Below" in ccsm > Window Rules, which has the problem that I can't pop it up while a window is maximized.


2) Awn-system-monitor has all kinds of gconf values about memory monitoring, but I can't actually get a memory monitor!  How do I do it?!

3) Finally, I have the problem that I can't make Alt-F1 pop up the main menu.  Is there a way to do that?

---

### Post by Zorgoth on 2010-08-06
Screenshot:

---

### Post by fabounet on 2010-08-06
with Cairo-Dock 2.2, you can have several docks at once, and configure them independantly.
You could replace the side dock with a 2nd Cairo-Dock then, and have the behavior you want then.

---

### Post by Zorgoth on 2010-08-06
I prefer AWN's notification area/daemon, main menu, and clock, so I would really like to get it working.  I also the simple theme for a side panel rather than another one like my flashy cairo-dock on the bottom.

---

### Post by Zorgoth on 2010-08-06
I also am having bugs in cairo-dock where the systray and cpu monitor applets, along with most other applets, do not display anything at all.

---

### Post by stinkeye on 2010-08-06
> **Zorgoth said:**
> I also am having bugs in cairo-dock where the systray and cpu monitor applets, along with most other applets, do not display anything at all.
That might have to do with the way you removed gnome-panel.

A better way to remove it is
gconf-edior /desktop/gnome/session/required_components
and remove the **gnome-panel** entry.

---

### Post by Zorgoth on 2010-08-06
That bug is older than the removal of gnome-panel.

But thank you!

---

