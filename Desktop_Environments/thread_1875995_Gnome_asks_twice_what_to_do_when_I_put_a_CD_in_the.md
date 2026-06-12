---
title: "Gnome asks twice what to do when I put a CD in the drive"
date: 2011-11-05
forum: Desktop Environments
---

### Post by cybergalvez on 2011-11-05
Hi all,
When I put a disk in the computer (or USB) I get asked twice what to do. Usually the CD will just open in Nautilus but then Gnome3 will ask me what to do too and I have to select something to make it go away.  How do I set it so the system only asks me once? I suspect its because something got left turned on when I installed gnome-shell over unity.

Any advise would be appreciated, this is one of those little irritations that just nags at the back of your head if you know what I mean

---

### Post by cbowman57 on 2011-11-05
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=206236&d=1320357515[/IMG]

Use dconf-editor and locate this entry, it's media-handling

---

### Post by cybergalvez on 2011-11-05
Thats exactly what I needed! 

Thanks!

---

### Post by cbowman57 on 2011-11-05
Glad it helped, quite a few people find the default behavior an annoyance.

---

### Post by cybergalvez on 2011-11-17
Ok I thought this was fixed, but apparently its not. Every time I insert a CD I get asked twice what to to do. Any way I can fix this? See attached image to see what I mean.

---

### Post by cbowman57 on 2011-11-17
System Settings > Removable Media

[ATTACH]207466[/ATTACH]

---

### Post by cybergalvez on 2011-11-20
not exactly what I was looking for, I don't mind that the computer asks, but what I am trying to figure out is how to only have one thing ask me, right now it looks like some GTK window (some unity remnant) or gnome-shell, but not both

---

