---
title: "Switch profile Bash to user . . ."
date: 2012-02-22
forum: Desktop Environments
---

### Post by waseembaraskar on 2012-02-22
Hi everyone out there,

I am novice to Linux.

While do some programming on terminal I switched to bash.
But didn't know how to go back to normal terminal.
My terminal shows -> bash- 2.3$   in user profile account.

I have created new user account, named "newuser1" where terminal show
[newuser@TRIMFSPE031 ~]$

I want to go to as [user@TRIMFSPE031 ~]$

How i will do that please help me out.

Very very thanx in advance. . . .

---

### Post by Lars Noodén on 2012-02-22
Did you accidentally change .bashrc?  If so, you can get a fresh copy from /etc/skel/.bashrc and restore from that.

---

### Post by waseembaraskar on 2012-03-08
thanx,

I restore the .bashsrc & .bash_profile file.
its working 


thanx.

---

