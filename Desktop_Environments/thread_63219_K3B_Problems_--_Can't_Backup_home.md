---
title: "K3B Problems -- Can't Backup /home"
date: 2005-09-07
forum: Desktop Environments
---

### Post by tilleyrw on 2005-09-07
After installing K3B on my Kubuntu 5.04 system, a problem occurred.

When clicking in the directory window to activate it, then pressing ctrl+A, then dragging the selection to the CD window -- K3B froze.  I should not say "froze", as that comes from by Windows experience.  K3B became extremely slow and required about 15 minutes to add the contents of my /home/[user] directory to the to-be-burned window.

I need to backup every file in my home directory, even the invisible files/dirs.  What will help me do this?

Thanks, Bob

---

### Post by jeremy on 2005-09-07
It may be that the ~ /.kde/share/apps/k3b/temp or some other file or dir keeps changing during this process. Can you try excluding this dir from the backup?

---

