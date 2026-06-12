---
title: "cannot edit /etc/sudoers"
date: 2006-06-17
forum: Desktop Environments
---

### Post by unisol on 2006-06-17
i am have trouble with root and password authenication when i try to edit /etc/sudoerd it is read-only anyone help

---

### Post by ayoli on 2006-06-17
sudoers file must be edited with visudo as root, type in a term:

sudo visudo

---

### Post by unisol on 2006-06-17
if i type that from a terminal i dont need to be in root is that correct

---

### Post by aysiu on 2006-06-17
Are you able to sudo?

If not, then this may help: [http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by hoodwink on 2006-06-17
[QUOTE=ayoli]sudoers file must be edited with visudo as root, type in a term:

sudo visudo[/QUOTE]
Normally ture, but I don't know about the "must" in that sentence.

For years I have just edited the file from root, ie

1. sudo su -
2. vi /etc/sudoers
3. make changes
4. write the file back with "w!" (yes, as root, you can update the file even though it's marked as read only).

Someone who knows more than I may care to comment, but I've never had any probalems with this procedure on any Linux distro.

---

### Post by Ramses de Norre on 2006-06-17
visudo scans the file for syntax errors after editing, that's the advantage.

---

