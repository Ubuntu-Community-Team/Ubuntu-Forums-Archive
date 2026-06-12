---
title: "Kubuntu KDE3 login/logout script"
date: 2009-02-27
forum: General Help
---

### Post by Azguz Bloodfist on 2009-02-27
I want to have a script that executes when I (the sole user of my system) logs in or out of kubuntu. It's KDE3 on Hardy.

Do I need to use .bash_login and .bash_logout? I use zsh - does it make a difference? I only want the script to execute when I log in/out, not every time I open/close a shell.

Cheers

---

### Post by Xiong Chiamiov on 2009-02-28
If you use zsh as your login shell, rather than bash, then the special bash files won't ever be read.

---

