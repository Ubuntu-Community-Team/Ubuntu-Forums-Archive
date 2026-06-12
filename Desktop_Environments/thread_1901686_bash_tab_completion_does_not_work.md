---
title: "bash tab completion does not work"
date: 2011-12-29
forum: Desktop Environments
---

### Post by adit on 2011-12-29
After typing
```
man ap
```
if I press tab twice nothing happens.  Same thing after typing
```
sudo ap
```
But if I simply type
```
ap
```
and press tab twice I get completions.

---

### Post by adit on 2011-12-31
BUMP

This problem started after I deleted hidden files (files that start with a dot) in my home directory.

---

### Post by dentaku65 on 2011-12-31
> **adit said:**
> BUMP

This problem started after I deleted hidden files (files that start with a dot) in my home directory.

You have deleted *.bashrc* file.
It's hard to recover everything after such operation (deleted all hidden files in your /home/<you>); probably you'll have other dysfunctions as well.

You can "recover" .bashrc file creating another user (profile) and then copy on your user (profile) that file.

Good luck.

---

### Post by adit on 2011-12-31
```
cp /etc/skel/{.bashrc,.bash_logout,.profile} ~/ && . ~/.bashrc
```
The above code worked.  Problem solved.

---

