---
title: "Trash can't delete."
date: 2009-01-17
forum: General Help
---

### Post by chrispche on 2009-01-17
I have a folder in my home directory that won't delete. This is due to permissions. If I sudo nautilus where is the home folder's trash located so I can delete the folder as root.

---

### Post by adult swim on 2009-01-17
/home/chris/.local/share/Trash/files

---

### Post by chrispche on 2009-01-17
Thanks.

---

### Post by jerome1232 on 2009-01-17
Except if you delete it in root nautilus all your really doing is moving it to root's trash.

Hold shift when you delete it to bypass trash, if you already moved it to root's trash, it's located at /root/.local/share/Trash. You might want to shift+delete it there.

---

