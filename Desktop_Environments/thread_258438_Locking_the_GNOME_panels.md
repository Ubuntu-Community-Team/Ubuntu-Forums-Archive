---
title: "Locking the GNOME panels"
date: 2006-09-15
forum: Desktop Environments
---

### Post by srunni on 2006-09-15
Is there any way to "lock" the GNOME panels so that they can't be dragged from their current location to another edge of the screen?

---

### Post by Christopher Cook on 2006-09-16
I don't think so, but I don't have dragging issues.

---

### Post by Super King on 2006-09-16
I don't have GNOME in front of me right now but you should be able to right click on the panel and choose 'Lock' or something similar. Otherwise right-click on the panel and go to Preferences and look in there.

---

### Post by srunni on 2006-09-16
I looked into that, and can't see anything about locking the panel into place. Any other suggestions?

---

### Post by orb9220 on 2006-09-16
Applets in panels can be locked but panels cannot be locked, Has this been considered and rejected?

Would seem like a good idea.

They will stay were you put them tho. I have 3 panels over two monitors and they always come up where I had them last.

Are you having problems with them?

---

### Post by srunni on 2006-09-17
It's not me, it's someone who I set up Ubuntu for (I use Kubuntu ;) ). It seems that the panels just move when he's using his computer without him even realizing. I'm not sure how that exactly works, but he's not really computer oriented, so it's not like I can say "just watch out for when you accidentally drag the panel to another edge," because most people don't even pay attention to that type of thing.

---

### Post by brallan on 2006-09-21
yeah, i have a similar problem, on linux computers being used in a social center the panels are ALWAYS rearranged. Drag and drop panels are DEFINITELY a drag ;) under circumstances where many people use the computers. This is not just a problem of dragging it back into place, since two things prevent this.

First of all, the panel may not be full of applets on the top/bottom of the screen, but when dragged to the side becomes full, preventing you from dragging and dropping it back. The only way to get it back to it's original position seems to be to delete one or more buttons until you have an empty space with which to drag it, and then read those buttons.

Second of all, the applets are rearranged even though they may themselves be locked. :( To put them back in their original positions one then needs to unlck them. ARRRRGHH!

There must be some kind of configuration file that can be locked, no?

It would be nice to have some way to lock the appearance of communal computers so that it only changes on sudo. Please help!

brian

---

### Post by skymt on 2006-09-21
Install [Sabayon](http://www.gnome.org/projects/sabayon/) from Synaptic.

---

### Post by srunni on 2006-09-21
> **skymt said:**
> Install [Sabayon](http://www.gnome.org/projects/sabayon/) from Synaptic.

The problem isn't that I don't know how to edit the configuration files, I can do that just fine. It's just that I don't know if it's even possible to lock the panels. I've searched Google numerous times with no results (which is why I came here). I was hoping that one of the more experienced users here might have an idea as to how this can be done. If I can confirm this isn't possible, then I just might suggest the addition of this feature to the GNOME developers. ;)

---

### Post by skymt on 2006-09-21
Sabayon lets you lock GConf entries, and panel location is stored in GConf. I haven't personally tried it, but it really should work.

---

### Post by cptnapalm on 2006-09-21
I've had this same problem.  On my machine, how it worked was that I would click an icon on the panel and then move the mouse.  Then the panel would magically appear at the bottom.

---

### Post by srunni on 2006-09-22
> **skymt said:**
> Sabayon lets you lock GConf entries, and panel location is stored in GConf. I haven't personally tried it, but it really should work.

Oh, I see. In that case, I might try it. Thanks for the help.

---

### Post by brallan on 2008-05-10
hit Alt-F2 and run gconf-editor

when you run it navigate to

apps->panel->global

under lock_down click the checkbox

and restart gnome with Ctrl-Alt-Backspace

much thanks to ##gnome and #ubuntu on irc.freenode.net for help with this one

---

