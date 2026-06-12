---
title: "deleting directorys"
date: 2010-07-26
forum: Desktop Environments
---

### Post by xletswinx on 2010-07-26
How do i remove directorys off of ubuntu?

---

### Post by linux18 on 2010-07-26
right click and delete OR
rm -r "directory"

---

### Post by KdotJ on 2010-07-26
> **linux18 said:**
> rm -r "directory"

Just as a word of warning, but VERY careful when using such commands. Commands featuring

> rm -r ......

and

> rm -rf ......
 
can be very dangerous, and infact just wipe out all data without asking if used incorrectly. As a break down, the code "rm" means remove, the flag "-r" means recursively so it will go through all sub-directories too. and the flag "-f" means force, which will do things without your confirmation.

Just be warned.

---

### Post by linux18 on 2010-07-26
> **KdotJ said:**
> Just as a word of warning, but VERY careful when using such commands. Commands featuring



and


 
can be very dangerous, and infact just wipe out all data without asking if used incorrectly. As a break down, the code "rm" means remove, the flag "-r" means recursively so it will go through all sub-directories too. and the flag "-f" means force, which will do things without your confirmation.

Just be warned.
" sudo rm -rf / " no longer makes your computer disintergrate, it just gives you the message " cannot remove root directory " try it in virtualbox if you don't believe me, that kind of malicious command has been secured long ago. just saying

---

### Post by Zeike on 2010-07-26
> **linux18 said:**
> " sudo rm -rf / " no longer makes your computer disintergrate, it just gives you the message " cannot remove root directory " try it in virtualbox if you don't believe me, that kind of malicious command has been secured long ago. just saying

Just because you can't 'rm -rf /' doesnt mean you can't still screw things up with the rm command.

---

### Post by linux18 on 2010-07-26
> **Zeike said:**
> Just because you can't 'rm -rf /' doesnt mean you can't still screw things up with the rm command.
true

---

### Post by KdotJ on 2010-07-26
> **linux18 said:**
> " sudo rm -rf / " no longer makes your computer disintergrate, it just gives you the message " cannot remove root directory " try it in virtualbox if you don't believe me, that kind of malicious command has been secured long ago. just saying

True, but how about when we're not talking about the root directory? For example, let's say you have a folder in your home folder called "dir1" and you want to recursively remove it. 

You use the command:

```
rm -rf /home/user/dir1
```

that will be fine, and will give the result you're after.
But let's say, by accident you add a space in there like so:

```
rm -rf /home/user/ dir1
```

This command above will wipe your entire home folder, along with dir1. Everything gone. So for the root directory yes it's now safe perhaps to an extent, but still worth mentioning the power of this command to new people

---

