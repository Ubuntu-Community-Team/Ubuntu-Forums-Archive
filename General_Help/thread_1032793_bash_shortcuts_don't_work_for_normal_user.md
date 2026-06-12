---
title: "bash shortcuts don't work for normal user"
date: 2009-01-06
forum: General Help
---

### Post by mcbenton on 2009-01-06
Running 7.10 server.  When I SSH from my admin account my bash shell color codes files and I have full access to normal bash keyboard shortcuts (e.g. up arrow for command history, etc.).

Today I created a normal user account like so:

useradd -m -c 'New User' newuser

When I log into the server using SSH with this new account I don't get any bash shortcuts.  Nor do other commands work, e.g.

$ history
-sh: history: not found
$ shopt
-sh: shopt: not found

I compared the .bashrc file for the new user and my admin user and they are identical.

Any ideas?  Thanks!!!

---

### Post by karlr42 on 2009-01-06
Sounds like that user isn't using bash as the default shell, for some reason. 
To confirm, could you type "bash" at that prompt and see if you get a bash shell(colours, history, etc..)?

---

### Post by dcstar on 2009-01-06
> **karlr42 said:**
> Sounds like that user isn't using bash as the default shell, for some reason. 
To confirm, could you type "bash" at that prompt and see if you get a bash shell(colours, history, etc..)?

This will show what shell is running:
```
set | grep SHELL
```

---

### Post by Ahadiel on 2009-01-06
> **mcbenton said:**
> Running 7.10 server.  When I SSH from my admin account my bash shell color codes files and I have full access to normal bash keyboard shortcuts (e.g. up arrow for command history, etc.).

Today I created a normal user account like so:

useradd -m -c 'New User' newuser

When I log into the server using SSH with this new account I don't get any bash shortcuts.  Nor do other commands work, e.g.

$ history
-sh: history: not found
$ shopt
-sh: shopt: not found

I compared the .bashrc file for the new user and my admin user and they are identical.

Any ideas?  Thanks!!!
You probably didn't set the shell for the user. I usually use *adduser* as opposed to *useradd* so I'm not too much of a help, but I'm sure the manpage would be.

---

### Post by lamachine on 2010-10-10
I've had the same problem. The new created user didn't use bash as default system, taping the &#8220;bash&#8221; command fix all.

---

### Post by zenthanian on 2010-12-22
The bash command worked for me, but defaulted back to the default shell the next time I logged in.  After searching some more I found this:

chsh -s /bin/bash
from [http://ubuntuforums.org/showthread.php?t=1578404](http://ubuntuforums.org/showthread.php?t=1578404)

---

