---
title: "Unprivilaged root"
date: 2009-06-04
forum: General Help
---

### Post by techgeek314 on 2009-06-04
I have a netbook dual booted with Windows XP and Ubuntu.  The dual boot setup works just fine.  I have set it up so that I can log in as root (don't yell at me).  The windows partition automatically mounts to /windows at boot, and the owner of the folder is root.  When I log in to root and try to change the owner and group, though, it just changes it back to root and the group that I already had!  Is there a way to change the owner?

Also, I have my user's home folder shared with another windows computer via samba.  The connection works fine, but when I boot Ubuntu and it automatically logs into my normal user, it tells me that I'm not supposed to allow other users to have access to my home folder.  This is just an annoyance (I can just ignore the message) but does anyone have a solution?

Thanks!

---

### Post by Megrimn on 2009-06-04
you may want to try logging in as an administrator instead of root when you change the owner and group, and use your administrative password when it asks for it.

---

