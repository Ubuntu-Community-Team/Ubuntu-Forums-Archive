---
title: "Desktop task bar is screwy... How and why?"
date: 2010-09-08
forum: Desktop Environments
---

### Post by SandWrrm on 2010-09-08
I have an HP pavilion, Windows 7 laptop that I dual-booted with Lucid a couple months ago. So far all is well, aside from the fact that every once in a while, the upper taskbar on my desktop freaks out. Usually, a black "break" looking box-thing appears in front of the internet icon, and right now it also morphed the power icon with my profile icon (I think that's what it is, anyway...) so that I can't see the power icon. Here's a screenshot, if it helps:
[IMG]file:///tmp/moz-screenshot.png[/IMG][ATTACH]168870[/ATTACH]

I don't know how to make it go away, much less make it stop forever.

---

### Post by randallecook on 2010-09-08
The same thing is happening on my system, at this very moment. Basically certain upper taskbar/panel items on the right side are duplicated in the space to the right, where another item used to be. Consequently, the menu I use to choose shutdown has been replaced with another copy of the menu with IM status options. I also have two copies of the date/time/calendar item. Not good.

I run Ubuntu 10.04 both at home and at work, and it has occurred in both places. It started about 2-3 months ago. Sometimes it happens when I start up, sometimes things are normal. I always install all the updates. Both systems have been upgraded from earlier Ubuntu versions.

To work around this problem, I have resorted to four things:

1. Hit the power button on the computer itself and choose shutdown in the dialog box that appears.

2. Add "Indicator Applet Session" to the panel to get a new shutdown menu to appear.

3. Run 'gnome-session-save --shutdown-dialog' from a terminal window.

4. I tried deleting what I guessed to be relevant "dotfiles" from my home directory (basically anything having to do with gnome). These are files and folders that start with a period and contains settings. This helped a little, but it still happens.

The cause is clearly a bug in gnome. Hopefully someone can provide some advice to clear this up, or else escalate the issue so it gets investigated and solved. I would hate to have to reinstall Ubuntu just to fix a GUI glitch.

Randall

---

### Post by DrMelon on 2010-09-08
A quick temporary fix for me is to right click on the bar in question, choose properties, and then show the hide arrows. Then, hide them again.

---

### Post by randallecook on 2010-09-08
DrMelon,

That did the trick! The panel redrew itself properly and all is well. Thanks for the tip!

Randall

---

### Post by SandWrrm on 2010-09-08
Thanks guys! That fixed it right up. I still wish I knew what was happening to it, but at least I can make it go away now .

---

