---
title: "Nautilus Templates Don't Work - more"
date: 2009-01-28
forum: General Help
---

### Post by triplemaya on 2009-01-28
Hi. Nautilus Templates Don't Work for me, and I found an old thread with that title, at

[http://ubuntuforums.org/showthread.php?t=181519](http://ubuntuforums.org/showthread.php?t=181519)

in which zeasier finds a solution, but it does not work for me.

I put templates in a correctly named folder, ~/Templates, but nothing in the right click menu. Wondering if this might be a different file system problem, since I have /home on a separate partition, I take zeasier's advice and put a Templates folder on the local file system, and link to it with ln -s. Nothing. However, for simplicity I used /root/Templates, which of course is mounted on /, and simply put templates in there and linked to it, and, as root everything is ok. Right clicking in the nautilus window I am running as sudo nautilus & gives me all the templates available. But nothing in my own home directory as ordinary user!? I changed all the permissions of the /root/Templates folder and contained files to my ownership and permissions for full read and write but this did not help either.

---

### Post by rahul_bhise on 2009-04-17
sudo gedit /home/<username>/.config/user-dirs.dirs

then edit this line
XDG_TEMPLATES_DIR="$HOME"

to
XDG_TEMPLATES_DIR="$HOME/Templates"

then put your all "Templates" folder content in /home/<username>/Templates

---

### Post by triplemaya on 2009-04-17
Many thanks rahul, works a treat. :D

---

