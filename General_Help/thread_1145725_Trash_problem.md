---
title: "Trash problem"
date: 2009-05-01
forum: General Help
---

### Post by B4RR13N705 on 2009-05-01
Hi, ive just deleted a file to the trash. The problem is, that when i try to clear the trash, it says that i dont have enought privilegies to delelte the file. Is there a way to "sudo" empty trash?

---

### Post by drs305 on 2009-05-01
> **B4RR13N705 said:**
> Hi, ive just deleted a file to the trash. The problem is, that when i try to clear the trash, it says that i dont have enought privilegies to delelte the file. Is there a way to "sudo" empty trash?

The safest is probably:
```
gksudo nautilus /root/.local/share/Trash/files
```
You can move up a level or two and delete both the *files* and *info* folders, and even the *Trash* folder if you wish. It will be recreated the next time root deletes something.

Use SHIFT-DEL to remove the trash. If you just hit delete it will move to ... the trash. USE CAUTION: SHIFT-DEL permanently removes the trash. If you delete the wrong folder, you can't get it back.

You can use "sudo rm" and point to the same address above but I don't generally write that command out.

Check out the link in my signature line to a guide all about finding and deleting trash.

---

### Post by B4RR13N705 on 2009-05-02
Thanx! your command works!

---

