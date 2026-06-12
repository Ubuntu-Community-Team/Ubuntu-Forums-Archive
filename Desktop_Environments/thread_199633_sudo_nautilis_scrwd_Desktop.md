---
title: "sudo nautilis scr*w*d Desktop?"
date: 2006-06-19
forum: Desktop Environments
---

### Post by eentonig on 2006-06-19
After using "sudo nautilus", I noticed all my desktop items are gone. background, icons, settings... All have gone somehow. Allthough when searching the filesystem, I can still see everything in it's place.

Anybody know what could have happened?

---

### Post by ajgreeny on 2006-06-19
I seem to remember reading somewhere on this forum that for greater safety, when starting gnome gui progs as root you should use *gksudo* instead of sudo, and for kde gui progs as root, it should be *kdesu* instead of sudo.  This is now what I always do without problems, but whether or not this is the cause of your difficulties I don't know.

---

### Post by eentonig on 2006-06-19
As I entered the command, I remembered this as well. The problem now arises on how to solve this issue I created myself.

---

### Post by munckfish on 2006-06-19
Have you checked the file ownership and access permissions of the items you can no longer see?

I've not experienced exactly this issue before but I have had similar problems on other systems where running as root has changed the access permissions on files inside my home directory so that they are no longer owned by my normal user account. E.g this happened to my bash_history file a couple of times and on Fedora the .ICEauthority file sometimes got snatched by root and I couldn't log in to Gnome.

---

