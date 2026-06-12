---
title: "Live disk, rescue option"
date: 2006-08-05
forum: Desktop Environments
---

### Post by meanmrmustard on 2006-08-05
I'm trying to use the live/install disk to fix a Dapper installation that has gone wrong.

Instructions on the live disk tell me to type "rescue" at the "boot:" prompt.
My question is how do I get to a "boot:" prompt when booting to the live disk? :confused:

Thanks
Mr Mustard

---

### Post by 5-HT on 2006-08-05
Pressing 'Esc' at the live CD menu should do the trick.

---

### Post by meanmrmustard on 2006-08-05
Thank you!

Where should I have found that bit of information?

Just one thing....
After entering "rescue" at the prompt - as instructed - it tells me "Could not find kernel image: rescue"

What am I doing wrong?

---

### Post by 5-HT on 2006-08-06
Getting the same thing on my end. Looks like the rescue option has been taken out of the Desktop live/install CD. There is a rescue option on the Alternate install CD, if you have it.
If not, what are you trying to fix? Most issues can be fixed from a live CD and chrooting into your install if necessary.

---

### Post by meanmrmustard on 2006-08-06
That's what I finally did - with a Knoppix disc. Grub had gotten confused - I straightend it out.

---

