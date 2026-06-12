---
title: "How to initialize $PATH and working directory in Terminal app?"
date: 2010-10-20
forum: Desktop Environments
---

### Post by adummy on 2010-10-20
[SIZE=3]I find myself keep typing the same **cd ...** and **export ...** commands when I start a new Terminal app. Is it possible to put these commands somewhere so they will be done automatically whenever a new Terminal is started? Thanks![/SIZE]

---

### Post by coabiguy on 2010-10-20
These types of commands are typically set via a profile.
You have two types of profiles as I understand them.
There is an all users profile that is executed regardless of the user who is logged on and a user-specific profile.

The actual file names depend on the shell you are using.
The default shell ( $ echo $SHELL ) is the bash shell
If you have not changed the default shell, then this link is a good start.

[http://www.cyberciti.biz/faq/change-bash-profile/](http://www.cyberciti.biz/faq/change-bash-profile/)

:popcorn:

---

### Post by kerry_s on 2010-10-20
> **adummy said:**
> [SIZE=3]I find myself keep typing the same **cd ...** and **export ...** commands when I start a new Terminal app. Is it possible to put these commands somewhere so they will be done automatically whenever a new Terminal is started? Thanks![/SIZE]

gnome-terminal --working-directory=/path/to

---

