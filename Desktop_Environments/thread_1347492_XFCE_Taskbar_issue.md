---
title: "XFCE Taskbar issue"
date: 2009-12-06
forum: Desktop Environments
---

### Post by Chico25 on 2009-12-06
Hi all,

Just recently I made a choice to switch from Debian Lenny to Xubuntu Karmic and.. well i've been trying to get my system working at least to certain extent ever since.

Amongst the issues i'm struggling is the funny problem with XFCE taskbar that sometimes works, and sometimes does not. I tried to delete settings, log off, kill apps that are highlighted when it stops working, no luck. 

The problem begins unexpectedly during normal operation, when nothing specific happens. It has the following symptoms:

- at least one item in the task bar is highlighted (or, to be precise, the background of the item is dimmed, so it's dark gray, but the item itself is not selected - looks like a notification),
- if i try to select any item at all (regardless - highlighted or not), it briefly appears selected on the task bar and then, the selection goes back to previously selected app. No action is taken by the window manager, so no window pops up (action completely ignored),
- if i kill all the highlighted apps (close them manually), then for a short period of time i actually can use the taskbar, but most often, the next time i select any window, it becomes both selected and highlighted, so i again lose the most basic functionality of the task bar.

i have no clue what else to try to get rid of this issue; erasing configuration did not help at all, and i'm running a fresh install of the os... 
i'd be very thankful if someone had some idea what else could fix that..

thanks bunches,
tomek

EDIT:
i cannot use window list, either. alt+tab is the only way for me to switch tasks, so i assume this may be more a window manager issue than taskbar, but then - window manager switches windows, if i use keyboard, so...

---

### Post by Chico25 on 2009-12-10
Any suggestions, guys? any at all..?

this is really.. frustrating :(

thanks in advance...

---

### Post by vrkalak on 2009-12-10
I have used the Xfce desktop on several different distros ... Xubuntu included.

I have never encountered any problem such as you've mentioned.

Perhaps, you can checkout the main Xfce website ... [http://xfce.org](http://xfce.org)
They might have an answer or some insight into your problem.

---

### Post by slumbergod on 2009-12-10
I always find the taskbar does weird things. Sometimes I go to restart my system and instead of getting the full range of options, clicking Logoff asks me something about closing xfce panel. 

Then there are times when autohide doesn't work and the panel stays on top.

I wouldn't change to another environment cos xfce is exactly the environment I like.

My best friend is:
killall xfce4-panel followed by ALT-F2 with "xfce4-panel" to restart it.

---

