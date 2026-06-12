---
title: "Start/Stop deamons w/o sudo"
date: 2009-04-18
forum: General Help
---

### Post by GSMX on 2009-04-18
hello all,

I have a php-development environment, but i don't need deamons like apache/mysql start at every boot. I would like some gui/panel applet that lets me start those in one click. Comparable with WAMPServer on windows and NAMP on Mac.

In the best case, it's already somewhere on the internets, if so, i couldn't find it.

In a good case, somebody is already working on it.

In the worst case, I have to make it myself, but then I need to know: how could an application that's not root start en stop the servers??? How can i make a shortterm implementation with some shell script? (so not the whole "sudo /etc/init.d/apache2 start", but a shorter one (not an alias, as you still need root)). 



PS. I took apache and mysql as examples, but the main question is: how can i make services/deamons user-independent?

---

### Post by Alterax on 2009-04-18
Well, a caveat. I do not recommend this for production systems, due to security concerns.  But the fact is that these scripts must run as root to do their jobs.  So to do what you are requesting means that these scripts has to be run by a standard user as if by root.

The solution is the sticky bit.  It allows any user to run a script as if it were run by its owner.  You set it like this (using mysql as an example)

```
sudo chmod 1755 /etc/init.d/mysql

```
then any user can execute it as if they were root:

```
/etc/init.d/mysql stop
```

Just remember that this command can now be run by anyone with shell-level access to your system, so weigh in those considerations before you proceed!

--Alterax

---

### Post by GSMX on 2009-04-18
I am aware of changing chmod permissions, but I don't like the solution.

Because if i wanted to put this in a normal application, every user has to change these permissions themselves.

I would rather like something with the ownership of the files...

---

