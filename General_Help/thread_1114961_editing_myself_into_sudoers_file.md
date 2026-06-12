---
title: "editing myself into sudoers file"
date: 2009-04-03
forum: General Help
---

### Post by shortridge11 on 2009-04-03
I've searched the forums, but something about typing sudo into the search bar doesn't give specific results....heh

Right now, only the root has sudo access.  How do i edit a user into the sudoers file, so i can perform sudo x and not have the message "you are not in sudoers file...." come up?  I'm not too sure how to do this, if it involves editing myself into a group, or whatnot.  If a post exists that answers this question, please point me towards it, otherwise any help would be appreciated =D

---

### Post by taurus on 2009-04-03
No need to edit /etc/sudoers.  You just need to add yourself to group admin in /etc/group.

[http://www.psychocats.net/ubuntu/fixsudo#recoverymode](http://www.psychocats.net/ubuntu/fixsudo#recoverymode)

---

### Post by RoseKnight on 2009-04-03
I see the line: adm:x:4:user

how do I add another user to the group?

---

### Post by shortridge11 on 2009-04-03
oh wow that was easy. thanks! =D

---

