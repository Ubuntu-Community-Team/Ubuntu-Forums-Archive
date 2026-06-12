---
title: "execute script on login"
date: 2005-08-15
forum: Desktop Environments
---

### Post by jeremytaylor on 2005-08-15
Hi,
I have a script that sets up the necessary environment variables for my intel compilers... I want it to run on login. what's a good place to put it and how to i execute them, just like from the command line or is there another way?
thanks
Jeremy

---

### Post by PeP on 2005-08-15
depending on your shell (bash or zsh or find the foorc for foo:
~/.bashrc
~/.zshrc
(other users are not affected)

/etc/bashrc
/etc/zsh/zshenv
(system wide configuration unless users tell otherwise)

---

