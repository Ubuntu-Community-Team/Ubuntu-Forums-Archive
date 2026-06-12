---
title: "Gnome panel text-entries focus issues"
date: 2005-07-17
forum: Desktop Environments
---

### Post by jfuentes on 2005-07-17
Hi everybody, my english is not very good but i'll try my best.

 Background:
I'm developing an gnome-panel application, first i've started it in Fedora Core 2 (in the office) and now i wanted to carry the work with me to my home, i have a brand new Ubuntu system in my pc and i'm having problems with it.


The point is that the focus upon the "entry" of my app doesn't exist (later i've foud one weird way to get it), that was working very well in other distros using gnome, but in this case i wasn't lucky. I've tried lots of GTK+ programing tricks to find a solution with no succes.

The only way to get focus is by the following steps:

1.- start xine or xmms
2.- minimize all the windows, even the xmms or the xine that u opened first
3.- put the mouse cursor upon the panel (in any clear region of it) or directly upon my app.

that's the only way to be allowed to write something in the entry widget.


i've heard about similar bugs in other distros and gnome versions, i've spent a week trying to fix this  :roll: , i've thought tha was my mistake but..., i think now is a gnome-panel issue.

could anybody gimme any idea to find a solution?

thanks.

---

### Post by damonw5 on 2005-07-17
Your English is fine :)

You could try filing a bug at [http://bugzilla.ubuntu.com/](http://bugzilla.ubuntu.com/) if you think it is a bug specific to Ubuntu. Others will look at it and tell you if it is a problem with Gnome itself or Ubuntu.

---

### Post by damonw5 on 2005-07-17
[QUOTE=damonw5]Your English is fine :)

You could try filing a bug at [http://bugzilla.ubuntu.com/](http://bugzilla.ubuntu.com/) if you think it is a bug specific to Ubuntu. Others will look at it and tell you if it is a problem with Gnome itself or Ubuntu.[/QUOTE]
 Also try posting your question in the Programming Talk forum here: [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by jfuentes on 2005-07-18
[QUOTE=damonw5]Also try posting your question in the Programming Talk forum here: [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)[/QUOTE]
 Thanks a lot, if i can find any solution i'll post it here as soon as i can.

---

### Post by jfuentes on 2005-07-18
this is a fixing upon the steps that i wrote above:


u just got to minimize the xmms (the xine or both if u opened both), the rest can lay in the desktop, then u got the focus in the entry by puting the mouse's cursor opun the panel (in any clear region) or directly upon the app.


i'll try to get key events as the xmms and xine do, but i still thinking it should'nt  be that way.

anyway, like we do with the holes on the street in these lands (LatinAmerica):
nobody fix them  [-X  -> we avoid them   \\:D/  -> nobody get injured   :) -> everybody is happy and drink beer each friday  :grin:  and often we go to vote.  ](*,)

---

### Post by jfuentes on 2005-07-21
Hi everybody once again.

It wasn't a bug, in the new gnome the panel is disigned to don't grab the focus by a simple click, it has to get it by a _NET_ACTIVE_WINDOW (or something like this).

this is by pressing Ctrl+Alt+Tab (Principles Basics of Gnome2 using) and choosing the panel u want to get the focus or, inside the app using the 

panel_applet_request_focus (PANEL_APPLET ( THE_APPLET_ITSFELF ),
				   event->time);



function, inside the cb of the event "button_press_event", connected to the entry widget, thus the entry grab the focus by clicking it.


I ask to the moderators if they consider it appropiated to move this thread to another section of this site, if yes, i'm agree with it.


Thanks everybody for all.  \\:D/

---

