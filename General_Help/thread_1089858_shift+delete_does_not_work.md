---
title: "shift+delete does not work"
date: 2009-03-07
forum: General Help
---

### Post by abhinav.p on 2009-03-07
is there any reason why shift+delete does not delete a file/folder in one particular partition while it does in other partitions?.also rm command in terminal fails....

---

### Post by kellemes on 2009-03-07
> **abhinav.p said:**
> is there any reason why shift+delete does not delete a file/folder in one particular partition while it does in other partitions?.also rm command in terminal fails....

Define 'fails".
You get some feedback?

---

### Post by abhinav.p on 2009-03-08
rudimentary analysys shows i have overwritten the permissions after altering the fstab file.now when i tried to modify the permissions using
#sudo chmod ug+wxr DIRECTORY NAME,it is not resetting the permissions.neither is it showing any error.what should i do?

---

