---
title: "desktop"
date: 2006-06-09
forum: Desktop Environments
---

### Post by hellseeker on 2006-06-09
i just installed ubuntu 6.06 on my laptop and on my desktop it shows hda1, problem is hda1 is my windows xp partition and i dont want that to show on my desktop. ive tried removing it but i havent been able to figure it out. can any1 help?

---

### Post by 23meg on 2006-06-09
In gconf-editor set the value of this key to false: /apps/nautilus/desktop/volumes_visible

---

### Post by hellseeker on 2006-06-09
can you please be a bit more specific. im trying to get back into this linux this and im slightly lost. i used to be pretty good with red hat..(took a network admin course) but i havent used it in a while and im forgetting everything

---

### Post by hellseeker on 2006-06-09
i figured out how to open the editor. simple now that i think of it...should have thought of it earlier..

edit. correct me if im wrong but now when i mount a floppy or a cd it wont show up on the desktop. how would i view mounted devices. would it go under places? also i have a mounted fat32 partition, how come that didnt show up on the desktop or under places?
thanx for the help

---

### Post by 23meg on 2006-06-09
> edit. correct me if im wrong but now when i mount a floppy or a cd it wont show up on the desktop. how would i view mounted devices. would it go under places? also i have a mounted fat32 partition, how come that didnt show up on the desktop or under places?
thanx for the helpRight, it won't. You can view mounted devices in Places / Computer. 

If a certain partition didn't show up, it's probably because it's not correctly configured in your /etc/fstab file. Do a forum and wiki search for "fstab" (see my signature) and you'll find more info than you'll want on how to set it up.

---

