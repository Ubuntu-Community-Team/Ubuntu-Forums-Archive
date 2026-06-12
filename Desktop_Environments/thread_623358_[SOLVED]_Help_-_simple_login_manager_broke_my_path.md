---
title: "[SOLVED] Help - simple login manager broke my path"
date: 2007-11-25
forum: Desktop Environments
---

### Post by jludeman on 2007-11-25
I used package manager to get slim. After it installed it asked me it I wanted to replace GDM. Sure why not?

Since then I'm having to sudo almost everything. 
For example:

route -n
Command 'route' is available in '/sbin/route'
The command could not be located because '/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative priviledges associated with your user account.
bash: route: command not found

env | grep PATH
PATH=./:/bin:/usr/bin:/usr/local/bin:/usr/X11R6/bin

I think GDM must have been doing something to set my path for me but I don't know how to talk slim into doing the same thing.

I checked and my user is still a member of admin group.

---

### Post by jludeman on 2007-12-01
Not solved really. I just don't use simple login manager any more.

---

