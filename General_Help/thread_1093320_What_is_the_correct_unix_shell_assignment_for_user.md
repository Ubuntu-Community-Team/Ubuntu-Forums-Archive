---
title: "What is the correct unix shell assignment for users?"
date: 2009-03-11
forum: General Help
---

### Post by einstein on 2009-03-11
I should know the answer to this question but I don't and Googling doesn't seem to be helping.

What unix shell should be assigned for local users and/or for remote users (there is not a lot of difference between the two on my system)?  Adding users through Ubuntu Users and Groups, the default seems to be /bin/dash; Webmin's default is /bin/sh.  For some reason, I have been selecting /bin/bash.

Thanks in advance.

Dennis

---

### Post by heindsight on 2009-03-11
There's no right or wrong answer. On ubuntu, /bin/sh is symlinked to dash. For interactive use, bash is probably nicer to use as  login shell since it provides command history and commandline completion and other commandline editing features which dash don't have.

If you want, you could even install tcsh, ksh, zsh (or one of several other shells available in the repositories) to use as login shells.

---

