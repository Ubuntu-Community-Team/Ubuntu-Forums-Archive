---
title: "Gnome doesn't work"
date: 2005-11-24
forum: Desktop Environments
---

### Post by sloboda on 2005-11-24
Hi!
Since yesterday I'm not able to use gnome.
When I log in nautilus and gnome-panel crash and I can't do anything.
Notice that:

1) these errors appear with one user, the other user of the pc is ok
2) I've already removed .gnome .gnome2 .nautilus and every directory that seems related to gnome
3) if I use xfce, softwares like gedit and file-roller don't work, also them crash.

I don't know what I can do :( 
Can someone help me??

Greetings from Italy,
Sergej

---

### Post by kairu0 on 2005-11-24
I have a similar problem. I think I caused it by doing a "sudo -s" and then running the wrong program.

Your problem may have something to do with bad file ownership permissions in the user's home folder.

---

### Post by sloboda on 2005-11-24
The answer is: I have to delete the fille .recently_used in the home directory...

Sergej

---

