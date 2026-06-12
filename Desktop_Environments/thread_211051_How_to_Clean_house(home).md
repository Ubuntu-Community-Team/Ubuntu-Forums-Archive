---
title: "How to Clean house(/home)?"
date: 2006-07-07
forum: Desktop Environments
---

### Post by shane2peru on 2006-07-07
Ok, after several installs, backups, restores, etc....  How does one go about cleaning up the home directory?  I noticed in my .firefox folder there were about 5 xkdopa.defualt.odis type folders.  I noticed that 4 of the five had not been edited in the past three months, and one was current.  I concluded that they were from past reinstalls, or restores.  I must have other files like this in my home folder.  
1.  How do I know what is old, or from a previous restore?
2.  How do I get rid of them without deleteing all my files and starting with a fresh install?
3.  Does anyone know of a program that will do this?
4.  Is this a common problem?

Thanks!

Shane

---

### Post by aysiu on 2006-07-07
To clean up the Firefox problem, try [this](http://www.ubuntuforums.org/showthread.php?t=103930).

The Firefox profile duplicates is a common problem, but I don't think you should see other redundancies in your /home folder.

Certainly if you see *.config* folders that you think you don't need, rename them to *.config.old*. See if that has any adverse effects.

If it doesn't, go ahead and delete *.config.old*. If it does, rename it back to *.config*.

---

