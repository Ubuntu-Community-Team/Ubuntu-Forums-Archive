---
title: "running nautilus from browser application"
date: 2009-01-27
forum: Desktop Environments
---

### Post by okusi on 2009-01-27
i am migrating my intranet application to ubuntu linux.  one very handy thing that i could do under Windows&trade; was to launch the file explorer program from within a browser, so that users could be presented with all files in a client's folder.

i want to be able to do this using  ubuntu.  at the moment i am reduced to opening ftp windows, which is not a good interface for editing files.

is there a way i can launch nautilus from within a browser? i've tried using <? exec("/usr/bin/nautilus") ?> but this does nothing.

anyone have any useful comments or directions?

---

### Post by GrfyGrumpyBear on 2009-01-28
It's because of IE and Explorer being tightly integrated in XP. IE 7 deintegrated them, disabling that. Firefox/Epiphany with nautilus were never integrated, so this behavious is impossible.

---

### Post by okusi on 2009-04-26
i realise now that what i actually need is for javascript to be able to execute nautilus locally.

this should be possible, but my experiments thus far have failed! :(

anyone, any ideas?  this is a make or break for me in terms of migrating my office intranet from Windows&trade; to completely Ubuntu.

---

### Post by okusi on 2010-01-08
> **okusi said:**
> i realise now that what i actually need is for javascript to be able to execute nautilus locally.

this should be possible, but my experiments thus far have failed! :(

anyone, any ideas?  this is a make or break for me in terms of migrating my office intranet from Windows&trade; to completely Ubuntu.

this has got to be possible.  i mean, if google desktop can open documents and folders from within Firefox, us mortals must also be able to do it!!

is there a starving programmer out there looking for a challenge?

---

### Post by okusi on 2010-01-17
> **okusi said:**
> is there a starving programmer out there looking for a challenge?
apparently not! ;)

---

