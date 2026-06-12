---
title: "Can delete file in Trash"
date: 2006-06-10
forum: Desktop Environments
---

### Post by Clarencemark on 2006-06-10
I am having problem deleting the Easyubuntu folder that is currently sitting in Trash. I am being informed that it is because I do not have permission to delete. The owner is Root.

Help!

p.s. I am new to Ubuntu 6.06

---

### Post by Ramses de Norre on 2006-06-10
```
sudo chown username -R ~/.Trash
``` substitute "username" by your username and give in your user password if it asks one.

---

### Post by Clarencemark on 2006-06-10
It worked!!!!

Thank you.

---

