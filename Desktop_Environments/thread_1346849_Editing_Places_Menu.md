---
title: "Editing Places Menu"
date: 2009-12-05
forum: Desktop Environments
---

### Post by Scooter_X on 2009-12-05
Hey everyone. I'm running my system with 3 partitions: 1 for windows 7, 1 for Ubuntu and 1 for everything else. What I was hoping to do is up where it says 'Places' I wanted to re-map those folders to the 'Documents' or 'Music' folders in my 'everything else' partition. Anyone know how to do that? I've been playing around with it since yesterday, can't figure out quite how. I only seem to be able to edit 'Applications' and 'System' and only add folders within them, not add folders to the taskbar. I'd appreciate some help. Thanks in advance.

---

### Post by peepingtom on 2009-12-05
This config is in a hidden folder in your home folder

~/.config/user-dirs.dirs

gedit ~/.config/user-dirs.dirs

---

### Post by Scooter_X on 2009-12-05
Oh sweet!! Thanks!! I'll mark solved as soon as I get it working. (I being still new at this am likely to hose myself and require even more assistance) :D

---

### Post by Scooter_X on 2009-12-05
Ha. Told you I'd hose myself :D

As an example, let's use the 'Documents' folder

It showed originally:

*XDG_DOCUMENTS_DIR="$HOME/Documents"*

and I changed it to:

*XDG_DOCUMENTS_DIR="/media/data storage/Documents"*

and it opened the same folder as it was opening before I made the change. Even after a restart. Is there something wrong with my syntax? I saved the file after I edited it and everything. :P

---

### Post by Scooter_X on 2009-12-05
Holysnap I found something [here]("http://http://ubuntuforums.org/showthread.php?t=1343835&highlight=edit+places+menu") that fixed me.

Basically, when I'm in the file browser, on the left side it shows all those folders in the 'Places' menu. I can drag and drop, delete, rename and otherwise completely manipulate whatever is in that left hand menu. So, I dropped in the ones I wanted to be my Documents and Music folders, deleted the ones I didn't want and called it a day!

Now I feel dumb. I make things way harder than they ever need to be.

All the same though, thanks, peepingtom for your input.

---

### Post by peepingtom on 2009-12-06
aah sorry I'm still getting used to the whole volunteer support thing. I'll make sure to mention stuff like that in the future, I totally knew you could drag and drop and assumed you did too :D

I'm glad it worked out :D

---

### Post by Scooter_X on 2009-12-06
Hey no worries. Thanks anyway! ;)

---

