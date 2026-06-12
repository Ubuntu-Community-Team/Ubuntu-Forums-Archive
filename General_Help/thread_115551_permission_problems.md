---
title: "permission problems"
date: 2006-01-10
forum: General Help
---

### Post by seww on 2006-01-10
I have tried to mount 2 FAT32 hard drives with user permission but it doesn't work. i have tried to unmount them and fix my /etc/fstab but nothing seems to work.

another problem is, i have the same password for 'sudo' but not for 'su'. if i write 'su' in Terminal, i have to write in the root passwd, but if i type 'sudo' i need my user passwd. messed up or am i too newbie?

---

### Post by healychan on 2006-01-10
[QUOTE=seww]I have tried to mount 2 FAT32 hard drives with user permission but it doesn't work. i have tried to unmount them and fix my /etc/fstab but nothing seems to work.

another problem is, i have the same password for 'sudo' but not for 'su'. if i write 'su' in Terminal, i have to write in the root passwd, but if i type 'sudo' i need my user passwd. messed up or am i too newbie?[/QUOTE]

The root pwd in Ubuntu is the same as your user pwd.

Try ```
sudo su
``` instead of su.

---

### Post by Fittersman on 2006-02-06
you might need to edit your hosts file but i cant tell you where that is right now because my internet doesnt work on ubuntu so i am on windows :D

---

