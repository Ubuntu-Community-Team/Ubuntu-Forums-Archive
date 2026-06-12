---
title: "problem log in"
date: 2005-10-29
forum: Desktop Environments
---

### Post by mario.gomes on 2005-10-29
I recently installed 5.10 and I could log in fine until a few days ago.  Now I get an error message saying:

libgnomevfs-WARNING: unable to create ~/.gnome2 directory permission denied

I would appreciate if anyone can help me in resolving this problem.  I can log in to the failsafe terminal but it won't let me CD to the directory of the user.  It says that I don't have permission.  There might be a simple way to resolve this and I would appreciate if someone can help me.

Thanks in advance.

---

### Post by Ampersand on 2005-10-29
try something along these lines in a terminal:
```
sudo chown -R username /home/username
```
(replacing username with whatever name you use to log in to your computer).

---

