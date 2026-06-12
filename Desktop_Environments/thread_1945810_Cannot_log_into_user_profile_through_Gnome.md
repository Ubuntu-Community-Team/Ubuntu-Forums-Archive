---
title: "Cannot log into user profile through Gnome"
date: 2012-03-23
forum: Desktop Environments
---

### Post by Robertjm on 2012-03-23
Hi all,

I had my system crash this morning. After restarting the computer, everything appears to be OK. However, when I click on my normal user, and then enter my password, the monitor flashes and then I end up back at the GDM choice of users.

I can log in just fine as Guest. In doing some searching, there were some notes about deleting the .Xauthority file from the home directory. I did that, and then also deleted the lock file within the /tmp folder. After shutting the machine completely down, I tried logging in again. But, that didn't help. 

If I hit ctl-alt-f1, I CAN log in to the shell, so I know my user does exist. Trying to use startx from here just gets me the msg about lock files.

Using Ubuntu 12.04 64bit

Robert

---

### Post by Robertjm on 2012-03-23
81 people viewed and no replies? Wow!

Anyways, a quick answer for anyone that digs this thread up in a search for the same problem.

There are three .Xauthority files in your home directory.

.Xauthority
.Xauthority-c
.Xauthority-l

You have to delete all three of them to fix the problem!

---

### Post by juanbisente on 2012-07-04
Thanks this works for me

---

