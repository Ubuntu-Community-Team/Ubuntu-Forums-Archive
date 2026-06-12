---
title: "Nautilus shows non-executable folders as empty???"
date: 2010-12-29
forum: Desktop Environments
---

### Post by u-slayer on 2010-12-29
Why should a folder have to be executable for nautilus to see it?

I was going crazy trying to figure out why my folder was full of files according to ls -lah, but nautilus showed the same folder as empty. Then I set the executable bit for the folder and all of a sudden nautilus can see it. 

Why should a folder even be executable? Isn't that bit supposed to be for programs? Also, isn't this a serious bug? I might have assumed the folder is empty because nautilus said so and then gone ahead and deleted that folder and destroyed all my data with it.

---

### Post by kellemes on 2010-12-29
Are these hidden files maybe? (preceded with a dot)
Nautilus shows these when pressing Ctrl-H

---

### Post by mcduck on 2010-12-29
> **u-slayer said:**
> Why should a folder have to be executable for nautilus to see it?

I was going crazy trying to figure out why my folder was full of files according to ls -lah, but nautilus showed the same folder as empty. Then I set the executable bit for the folder and all of a sudden nautilus can see it. 

Why should a folder even be executable? Isn't that bit supposed to be for programs? Also, isn't this a serious bug? I might have assumed the folder is empty because nautilus said so and then gone ahead and deleted that folder and destroyed all my data with it.

Viewing a directory's contents is same as executing the directory, thus you need the execute permissions to enter a directory.

(read permissions only make you able to access files inside a directory if you know the exact path and filename)

So no, that's not a bug, that's how directory permissions are supposed to work. They make a difference between accessing files inside a directory and being able to list contents of a directory. And same permissions of course apply to Nautilus (and any other graphical file manager) as well.

---

