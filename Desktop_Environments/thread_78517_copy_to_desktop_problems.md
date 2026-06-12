---
title: "copy to desktop problems"
date: 2005-10-18
forum: Desktop Environments
---

### Post by Trajan on 2005-10-18
I've been trying to find a solution for this problem.

I have a CD with some files that I wish to copy to my Ubuntu Desktop, but for some reason it tells me that "I do not have permissions to copy" the files unto the desktop.
I tried chmodding the folder but no luck. Has anyone had this problem before ? I don't want to log into windows to do this. :/

---

### Post by aysiu on 2005-10-19
Is this a music CD? If so, you may have to rip the tracks instead of just dragging them to the desktop. There's a program called Sound Juicer that can help you with this.

If it's really a permissions issue, try running this command ```
gksudo nautilus
```, then navigating to the CD and copying the files to the desktop.

---

### Post by Trajan on 2005-10-19
they're regular files. But after trying "gksudo nautilus".... it just doesn't copy everything into the desktop. Just a selected few files. Is there another way  ?

---

