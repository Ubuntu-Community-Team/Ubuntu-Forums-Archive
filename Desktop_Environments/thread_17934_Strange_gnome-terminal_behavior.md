---
title: "Strange gnome-terminal behavior"
date: 2005-03-03
forum: Desktop Environments
---

### Post by slaughterc on 2005-03-03
I am seeing strange behavior in the gnome-terminal.  If you set a new environment (for example export MYVAR=123), and then start another gnome-terminal, MYVAR is not in the environment, and the original gnome-terminal returns to the prompt.  If you start an xterm (or even a konsole), MYVAR is defined, and the original gnome-terminal does not return the prompt until the xterm or konsole has closed.

Also, if you do a sudo gnome-terminal, MYVAR is also defined and the prompt does not return until you exit the new gnome-terminal.

How can I get a new gnome-terminal, as my userid, to keep the environment from the parent?

---

### Post by slaughterc on 2005-03-03
I figured it out.  Starting with --disable-factory gives the behavior I am looking for.

---

