---
title: "Run commands on remote PC"
date: 2009-01-21
forum: General Help
---

### Post by supanatral on 2009-01-21
for windows, theres a neat little program called psExec and it allows an administrator to run a ms-dos command on a remote computer. Is there a similar program for ubuntu?

---

### Post by stefangr1 on 2009-01-21
In Ubuntu and Linux in general this is usually done with ssh (installed by default). On the server side, you have to install openssh-server.

---

### Post by supanatral on 2009-01-21
Thanks for your reply. I have ssh working from a pc to a linux box but thats not my issue. I want to run a command on a windows computer from linux. Sysinternals has a program that does this but its made for windows computers to connect to other windows computers.

---

### Post by amauk on 2009-01-21
remote desktop is going to be easiest

other options,
- install cygwin on the windows box & set up SSH on cygwin - then remote in just like linux-to-linux
- try running psexec in wine (although I'd say this is a long shot...)

---

### Post by felker2 on 2009-01-21
From the top of my head: I would use "rsh" to execute a command on another system.

So, google for "rsh for windows" ... it gives some useful hits.

---

### Post by inadaze on 2009-01-21
I am a big fan of rdesktop.  
I had a Windows XP machine that I needed to get to from my Ubuntu Intrepid machine and I installed rdesktop with no problem.  and it runs as simply as 
```
rdesktop -g 1124x980 192.168.xxx.xxx
```

You can set whatever resolution you want (even fullscreen).

cheers,
Jay

---

### Post by kevdog on 2009-01-21
Id second the cygwin recommendation.  It works exactly the same in windows as in linux.  Same config files, etc.  The security model is decent also.

---

