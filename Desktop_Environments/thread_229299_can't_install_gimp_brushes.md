---
title: "can't install gimp brushes"
date: 2006-08-04
forum: Desktop Environments
---

### Post by Szurgot on 2006-08-04
OK I'm trying to install brushes for the gimp. I have them all in one folder and i want to transfer all the contents of it to usr/share/gimp/2.0/brushes the problem is when i try it says i don't have permission to do this. how is that possible when I'm the admin on the computer and the one that installed the OS?? also i check the propeties on it. it says it's owner is root . and it won't allow me to change any of the permissions or anything.

---

### Post by Szurgot on 2006-08-04
anyone???

---

### Post by Szurgot on 2006-08-04
dmmit it looks like I'm screwed

---

### Post by gThree on 2006-08-04
3 Different Ways To Unscrew Yourself:

1 ... Put the brushes in .gimp-2.2/brushes
2 ... Launch Nautilus from a Terminal with "gksudo Nautilus"
3 ... Use CLI, as in entering "sudo mv [brushesHere] [brushesGoThere]" in a Terminal

In #1, user can alter home folder.  .gimp-2.2 is an "invisible" folder.  Enable viewing by checking View >> Show Hidden Files (if you haven't yet).

In #2/#3, user becomes Super User and runs either Nautilus or CLI to perform the operation.  If you're not familiar with CLI/or "mv", run "man mv" in Terminal before you try anything.

---

### Post by trucker33377 on 2008-07-11
this is an old post but i have the same problem i want to add brushes would i follow this? is there something diff i should do?

---

