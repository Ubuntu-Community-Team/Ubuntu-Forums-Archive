---
title: "Automatically applying gnome emblems"
date: 2007-11-05
forum: Desktop Environments
---

### Post by paul.maddox on 2007-11-05
Hi,

I have a large folder of TV shows which I seem to have trouble keeping track of which episodes i've watched and which ones I haven't.

The best solution I've found so far is to apply a gnome emblem to the ones I've watched. This works well but is a bit tedious to do (Right click -> Properties -> Emblems -> Pick Emblem -> Save).

Is there some way I could get mplayer to automatically apply an emblem to a file when it's opened? Maybe by creating a wrapper script to do the emblem tagging. 

How does gnome keep track of which files display emblems? Is this held in gconf?


Thanks,

Paul

---

### Post by gsiliceo on 2007-11-12
i dont know about a script but in nautilus you can be browsing your folders in the right side and in the left side have all the emblens ready to bo dragged and dropped. Click where it says placesv
Thats a little faster than right click > properties > etc

---

### Post by SQuark on 2007-11-24
> **paul.maddox said:**
> How does gnome keep track of which files display emblems? Is this held in gconf?


From Googling around, I think this information is kept in the .xml files in ~/.nautilus/metafiles.

(As a side note for anyone who's interested, Thunar stores it in ~/.cache/Thunar/metafile.tdb)

---

### Post by Endolith on 2008-05-25
> **gsiliceo said:**
> i dont know about a script but in nautilus you can be browsing your folders in the right side and in the left side have all the emblens ready to bo dragged and dropped. Click where it says placesv
Thats a little faster than right click > properties > etc

Ooh good tip.  You can also add custom emblems that way by dragging image files into the left-hand pane.

Are there any packages that include lots of other emblems?  The ones they provide aren't so useful for me.

I don't see any easy way to remove emblems, though.  [Edit: You can drag the same emblem onto a drive to remove it.  Not intuitive at all, but at least it's possible.]

Also, the emblems only appear in a certain view.  I'd like a drive to have the same emblem in the "Computer" view, on my Desktop, and in the left-hand side bar tree view.  Is there any way to make this happen automatically?

---

