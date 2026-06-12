---
title: "Where is the other .bash_history?"
date: 2009-01-23
forum: General Help
---

### Post by hardysummer on 2009-01-23
Open the first terminal.  Then open a second.  Whatever you type in the second terminal will not be recorded in ~/.bashrc_history.  Yet, you can get the previous commands in the second terminal with the Up key.

So where are the second terminal's commands being recorded?

---

### Post by heindsight on 2009-01-23
Bash only writes the commands you enter to .bash_history when you exit the shell.

---

