---
title: "GDM on Wayland does not fork login shell; can it be done?"
date: 2024-10-01
forum: Desktop Environments
---

### Post by matt-rw on 2024-10-01
I noticed that my environment variables defined in ~/.bash_profile don't show up in my Terminals.   I did a little research and found that GDM on X11 and other desktop managers do for a login shell, GDM on Wayland does not.
I also notice it's possible to add functionality in /etc/gdm3/PostLogin/Default and /etc/gdm3/PreSession/Default.  I'm asking if anyone knows how to use these or other methods to get ~/.bash_profile sourced.

---

### Post by him610 on 2024-10-01
Maybe this will help point you in a somewhat different direction, [https://askubuntu.com/questions/58814/how-do-i-add-environment-variables]("https://askubuntu.com/questions/58814/how-do-i-add-environment-variables")

---

### Post by matt-rw on 2024-10-01
Sure, putting them in .bashrc is a solution.  I was looking for something to be consistent w/ convention.  Any ideas?

---

### Post by him610 on 2024-10-02
You might consider putting them in *.bash_aliases*; although, I have only defined additional aliases in *.bash_aliases.*

---

