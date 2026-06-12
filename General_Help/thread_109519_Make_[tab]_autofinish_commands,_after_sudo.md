---
title: "Make [tab] autofinish commands, after sudo"
date: 2005-12-28
forum: General Help
---

### Post by kwaanens on 2005-12-28
One of the great shortcuts in console is you can just click [tab] to finish the first letter(s) in your command, og press it twice to list your options.
Now, on Ubuntu, using sudo, you lose some aspects of this feature.

It can't be that hard to make the console "ignore" sudo (and "gksudo"), and autofinish commands. So, how? And why isn't this feature already packaged in Ubuntu?

- Ketil

---

### Post by bjourne on 2005-12-28
Edit the file ~/.bashrc. There is a section that begins with "enable programmable completion" which is commented out. Comment it in. The reason it is not enabled by default is because it makes bash start sligthly slower.

---

### Post by sciurus on 2005-12-29
[QUOTE=bjourne]Edit the file ~/.bashrc. There is a section that begins with "enable programmable completion" which is commented out.[/QUOTE]

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).

---

### Post by jliedeka on 2005-12-29
You could just type sudo su, then your commands.

---

### Post by briancurtin on 2005-12-29
that isnt exactly a recommended approach, but it does the job if you cant figure out other ways

---

