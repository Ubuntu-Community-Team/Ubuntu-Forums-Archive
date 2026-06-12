---
title: "gnome session reset?"
date: 2006-05-27
forum: Desktop Environments
---

### Post by NESFreak on 2006-05-27
while i was searchin to change the kde apps language in gnome the kde ocnfiguration app crashed. i shut it down using teh powerbuttun and it shut down the normal way, but gome automaticaly saved my session including the coniguration app, so that it automaticaly starts when i start gnome. making gnome crash.

Now is the quetion: how do i stop the damn thing from starting everytime i boot?

---

### Post by mostwanted on 2006-05-27
If you use the resque boot option at GRUB you should be able to have cmd-line access to your PC. Navigate to your home folder and remove a hidden folder called .gnome2 (or similar, use *ls -a* to show the hidden folders). If that doesn't work, try creating a new directory in your home dir with *mkdir* and move all your hidden dirs into that like this

*mv .* newdir/*

where newdir is the name of the newdir you created.

The idea here is of course to default back to the original settings. If you can log in you can move the hidden folders back one by one to determine which one is faulty and needs to be removed.

---

