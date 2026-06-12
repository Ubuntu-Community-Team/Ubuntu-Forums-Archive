---
title: "Login/User Problem"
date: 2005-08-06
forum: Desktop Environments
---

### Post by MartinJ on 2005-08-06
I'm new to Linux and have been experimenting with Kubuntu for a few days.  However, I've messed something up and now can't log in to kde.

After loading linux, and entering my username and password into kdm I get an error message saying "Unable to login as root" or something similar.  I can log in using the console login but afterwards the command line shows the current user is root.

I'm fairly sure how I messed it up.  In KUser I added myself to the sudo group, from the next login this problem started.

I have tried to add a new user using useradd from the command line but I can't seem to get it to work correctly.

Can anyone help me get back into kde?  Thanks.

---

### Post by ph8 on 2005-08-06
[QUOTE=MartinJ]I'm new to Linux and have been experimenting with Kubuntu for a few days.  However, I've messed something up and now can't log in to kde.

After loading linux, and entering my username and password into kdm I get an error message saying "Unable to login as root" or something similar.  I can log in using the console login but afterwards the command line shows the current user is root.

I'm fairly sure how I messed it up.  In KUser I added myself to the sudo group, from the next login this problem started.

I have tried to add a new user using useradd from the command line but I can't seem to get it to work correctly.

Can anyone help me get back into kde?  Thanks.[/QUOTE]
 erm, this sounds bizarre.

For starters, it's my belief that the non-root user you create on Kubuntu install is automagically a member of the admin group, which in turn automatically gets sudo privileges. 

Also, you say you're logging in as 'nonrootuserA' and getting root powers? that's a little backwards? check/paste your /etc/passwd and any group files you've altered

---

### Post by MartinJ on 2005-08-07
Yeah, I'm logging in as "martin" but the command line shows root.  No group files altered but here's an extract from /etc/passwd:

root:x:0:0:root:/root:/bin/bash
martin:x:0:109:Martin Jones::

If it's easier, how would I create a new user from the console?

---

### Post by MartinJ on 2005-08-07
ok, figured it out.  No more problems

---

