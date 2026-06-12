---
title: "How to keep a task running after closing my remote login session?"
date: 2008-06-08
forum: Desktop Environments
---

### Post by cuthbertkao on 2008-06-08
Hi,

    How to keep a task running after closing my remote login session?

    For my work, I have to remote log into our Ubuntu server to run some tasks,  but, sometimes, one task may take  even more than one hour to finish. I would like to keep it running after I close my connection session. However, I couldn't find a way to do that.  Could transferring the owner of a running task to another user do that or is there any other way?  Thanks in advance.


Cuthbert

---

### Post by squaregoldfish on 2008-06-09
The nohup command is what you're after:

```
nohup <command> &
```

Will start the command, but it won't be killed when you log out. The standard output from the command is written to a file named nohup.out, so you can look at it later.

Steve.

---

### Post by kpkeerthi on 2008-06-09
Use [screen]("http://www.rackaid.com/resources/linux-tutorials/general-tutorials/linux-screen.cfm")

---

