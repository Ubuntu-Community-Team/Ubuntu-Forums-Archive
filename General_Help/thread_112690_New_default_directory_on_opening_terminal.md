---
title: "New default directory on opening terminal?"
date: 2006-01-04
forum: General Help
---

### Post by Marinmo on 2006-01-04
No idea how I managed to screw this up, but now whenever I open a terminal the starting directory is /etc instead of the "usual" one, ie /home/username

How did I manage to do this? I'm not entirely sure myself, but I sure don't like it! Anyone with an idea how to fix it back the way it was? :(

---

### Post by Tal on 2006-01-04
I've got a compile running, but I'd assume it's related to a .profile or something in your home directory. do an 'ls -al' after going into your home directory to see what preference files there are to edit.

---

### Post by professor_chaos on 2006-01-05
I could be wrong here, but I think (vaguely) that your directory is saved if you save layout at logout. I'm not sure about this, but I have too much I'm working on to test this.

---

