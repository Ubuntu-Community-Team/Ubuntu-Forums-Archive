---
title: "AAARGH! What happened to my folders?!? - chmod deep troubles"
date: 2006-01-07
forum: Desktop Environments
---

### Post by ominolore on 2006-01-07
Aaaargh!!!!
I was in need to fix the permission for my whole music archive at the end of loooooooooooong work for ripping / renaming and filling tags.. then i typed

[FONT="Courier New"]sudo chmod --recursive 644 Musica[/FONT]

(where "Musica" is the name of the root directory of my music archive)

and now all the folders are messed up. In Nautilus under the name of each folder "..." has replaced the number of items contained and if I go under the permission tab of each item a text says that the permission of that item cannot be determined. And I can't enter any directory anymore!!

PLEASE ANYBODY HELP ME!!!!!!!
THIS WORK TOOK ME A WHOLE WEEK!!!

---

### Post by tryrmdashrf on 2006-01-07
Folders must have the execute-bit set to be able to traverse them.

Do a chmod -R 655 Musica instead.

---

### Post by ominolore on 2006-01-07
I've just changed the permissions to 755 and everything's now back to normality.
Thank you so much for your help and sorry for my rash alarmism. I was just ignoring that fact. ;)

---

