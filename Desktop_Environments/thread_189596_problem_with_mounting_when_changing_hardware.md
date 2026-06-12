---
title: "problem with mounting when changing hardware"
date: 2006-06-05
forum: Desktop Environments
---

### Post by NiksaVel on 2006-06-05
Hey all,

I don't know if this is a known problem, or if it's just me not knowing my way around yet, but:

I have an old p2 that only has one IDE port working...  I have 2 HDDs and 1CD-rom

while installing xubuntu I had 1hdd and 1cd connected and it installed great...  when all was done, I shut down, unplugged the CD and connected the second hdd in it's place.

The gui progs recognised it just fine, no prob - gparted and disk-manager.
The problem was when I tried to mount it to a directory....

I created a dir inside my home dir and mounted it with disk manager and it mounted just fine - exept that it was all marked as owner=root and I had no permissions to work in it...   I couldn't even change the owner while I had root privilegies...


than I went to do it manually and looked at my fstab file (this part was of course after doing some reading here and hearing of the fstab file for the first time :mrgreen: ).

fstab had my hdb1 described as cd-rom, and not as a hdd

?????

after I manually rewrote the line it works okay, but shouldn't it get updated by itself?

---

