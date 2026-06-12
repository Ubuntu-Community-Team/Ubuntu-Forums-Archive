---
title: "moving ubuntu to another hdd"
date: 2006-03-15
forum: Desktop Environments
---

### Post by sopo_dan on 2006-03-15
let me start by explaining how my current config looks like:

sda+sdb form a raid0 matrix on wich i have installed win xp (c: & d: )
hda contains 4 partitons as follows: hda1 (ntfs), hda5 (/), hda6 (/home), hda7 (swap)
grub is in mbr of hda and only boots linux from hda5

i plan to move all of this to a new single sata harddrive (so i'd end up having only sda). first i thought i'd just make some images with ghost and then restore grub according to the related how-to in the how-to section
then it struck me that there must be alot of references throughout the whole system to the specific device name (/dev/hda5 for example) and that this time i'd need grub to be able to boot win xp as well
now i'm completely clueless about the whole thing

can anyone please explain, as noob-friendly as possible, what i should do?

---

### Post by sopo_dan on 2006-03-16
please, can noone help? :(

---

