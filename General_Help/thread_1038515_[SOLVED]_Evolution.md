---
title: "[SOLVED] Evolution"
date: 2009-01-12
forum: General Help
---

### Post by Trzone on 2009-01-12
I reinstalled without formatting my /home partition and now evolutions files and folders all are owned by root
is there a way to get all the files and folders in .evolution to be owned by me?
I'm comfortable with using the terminal!
thanks

---

### Post by patmalcolm91 on 2009-01-12
Chown is the command to change ownership of files, to change everything in .evolution, this should work (GROUP is your group name (usually the same as user name, it's the first word when you enter the command "groups"); USER is the username)

```
sudo chown -R USER:GROUP /home/USER/.evolution
```

---

### Post by Trzone on 2009-01-12
Thanks, although i'm still having issues
i have a really old backup file
Note: this is another good reason why i need to backup everything on a weekly basis :P

---

