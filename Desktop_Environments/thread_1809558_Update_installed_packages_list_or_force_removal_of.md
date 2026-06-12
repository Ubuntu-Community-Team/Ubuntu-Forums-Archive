---
title: "Update installed packages list or force removal of package?"
date: 2011-07-21
forum: Desktop Environments
---

### Post by cipherboy_loc on 2011-07-21
Okay, so I kinda screwed up here. I was working on my flash drive install of Ubuntu, when I squashfsed my /usr. Long story short, I some how ended up with a working /usr, but with a few packages marked as installed, but not having its components installed (emacs). When I try to remove emacs (emacs23-nox), it gives me numerous errors about files (all relating to emacs) not existing (all in /usr). Thus my questions are as follows:

1) Is there a way to force the removal without it caring about missing packages?
-OR-
2) Is there a way to reload which packages are installed by checking which files exist, etc?
-OR-
3) Should I just nuke and re-install?



Cipherboy

---

### Post by cipherboy_loc on 2011-07-21
Solution:

I edited /var/lib/dpkg/status with a different text editor, searched for all instances of emacs and deleted the corresponding lines. 



Cipherboy

---

