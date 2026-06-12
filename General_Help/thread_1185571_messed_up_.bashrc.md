---
title: "messed up .bashrc"
date: 2009-06-12
forum: General Help
---

### Post by rrobertt on 2009-06-12
when i open the terminal i get this, bash:1H~: command not found,
if i switch users it works fine. I wanted to see what was in the .bashrc so i did a cat and less command. Then I opened it with the vim editor and i saw something about a script and i saw cat and less so i deleted it all and saved and quit. I have no idea what i was really doing but now my terminal gets the error i mentioned earlier. what can i do to repair the .bashrc file? I'm using Ubuntu 9.04. thanks

---

### Post by statistic on 2009-06-12
If you jsut want to reset it to default, instead of deletng the contents of the.bashrc file, try deleting the file itself, then the next time you start bash, it should create you a fresh .bashrc

EDIT:Nope, no fresh .bashrc when I just tried that, but it didn't seem to damage anything either.
EDIT2: Sorry about that, I should have tested it before I posted it, however, removing it I believe (and appears to) make you fall back to the system's default bash settings. Anyways, if you copy out /etc/bash.bashrc to your home folder as .bashrc you'll have the default one back that you can edit from there as you like.

---

### Post by rrobertt on 2009-06-12
thanks for your help, copying the bash.bashrc file worked.

---

