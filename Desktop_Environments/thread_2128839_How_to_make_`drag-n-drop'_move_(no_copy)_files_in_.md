---
title: "How to make `drag-n-drop' move (no copy) files in xfce (thunar)."
date: 2013-03-24
forum: Desktop Environments
---

### Post by cookevillain on 2013-03-24
How does not set up the file manager in xfce so that a drag an drop operation moves the file/directory as opposed to copy it. Right clicking works but I would like this to be the default (i.e left clicking will do that). This thread:

[http://ubuntuforums.org/showthread.php?t=1012578](http://ubuntuforums.org/showthread.php?t=1012578)

concludes that this `mostly been solved' but I have no idea what has been solved: there is no advice on how to set up thunar (or whateve else) othar than the (terrible) option of `use right click and live with it'. The whole idea of moving away from the horrors of gnome3 and unity (and, probably eventually, ubuntu as well) is to avoid being locked into a `glorified dvd player-like' system and getting back to the days when one can actually set up the machine to his liking.

---

### Post by Toz on 2013-03-24
Which version of Xfce/thunar are you running? I recall this being a problem in that past, but I honestly didn't do enough drag/drop to notice (more of a CLI person). In fact there is a bug report open for this: [https://bugzilla.xfce.org/show_bug.cgi?id=9142]("https://bugzilla.xfce.org/show_bug.cgi?id=9142").

Having said that, I decided to give it a go on my system now (Xubuntu 13.04/Xfce 4.10/Thunar 1.6.2) and the drag/drop action _moves_ the file both from directory to directory and directory to desktop. However, it seems to _copy_ to both my ntfs partition and samba shares.

What are the source and destination directories that you are trying with?

---

### Post by Buntu Bunny on 2013-03-24
> **cookevillain said:**
> How does not set up the file manager in xfce so that a drag an drop operation moves the file/directory as opposed to copy it.... This thread:

[http://ubuntuforums.org/showthread.php?t=1012578](http://ubuntuforums.org/showthread.php?t=1012578)

concludes that this `mostly been solved' but I have no idea what has been solved: ...

I've been annoyed by the copy not move from desktop to file manger (Thunar), but the suggestion in the mentioned thread to hold down shift and then drag and drop, worked for me. No extra copy to delete from my desktop.

---

