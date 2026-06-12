---
title: "[SOLVED] Faces?"
date: 2006-08-28
forum: Desktop Environments
---

### Post by CatKiller on 2006-08-28
I have recently added some new users to my computer. I had previously set my own face using the About Me window. I've tried the same thing with the new users and although they can both see my face on the Change User screen, and they can both see their own faces, I can't see either of them and they can't see each other.

They've each got a .face in their home directories, made by the About Me tool, and as far as I can tell these have the same permissions as mine.:confused:

---

### Post by CatKiller on 2006-08-28
Anyone?

---

### Post by CatKiller on 2006-08-29
I managed to fix it: It seems that the add user app gives different permissions on the home folders than the installer. By allowing execution for others and group on the users' home folders, all the faces show up.

---

