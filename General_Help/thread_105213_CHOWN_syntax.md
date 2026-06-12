---
title: "CHOWN syntax"
date: 2005-12-17
forum: General Help
---

### Post by Cath0de on 2005-12-17
Well, I'm trying to change the ownership of a folder on my desktop from root to myself (username cath0de) so I can delete it, but I don't know the syntax of the chown bash  command!

Can someone help me out with that or maybe explain another way to delete a folder full of crap that is root owned?

---

### Post by towsonu2003 on 2005-12-17
```
sudo chown username:username /path/to/file
```

```
man chown
``` will give more than enough info on this. 

for folder and all its contents, ```
sudo chown -R username:username /path/to/folder 
``` BUT DO NOT DO THIS TO SYSTEM FOLDERS (read: anything aoutside /home/username/...

---

### Post by aysiu on 2005-12-17
If you just want to delete it, why bother changing ownership? Just do ```
sudo rm -r ~/Desktop/nameoffoldertodelete
```

---

### Post by towsonu2003 on 2005-12-18
[QUOTE=aysiu]If you just want to delete it, why bother changing ownership? Just do ```
sudo rm -r ~/Desktop/nameoffoldertodelete
```[/QUOTE]
Not that I don't trust OP's abilities but, I wouldn't use rm as root :) bad stuff happens when you make a typo :-#

---

### Post by aysiu on 2005-12-18
[QUOTE=towsonu2003]Not that I don't trust OP's abilities but, I wouldn't use rm as root :) bad stuff happens when you make a typo :-#[/QUOTE] Ah. Good point. Chown is safer.

---

### Post by cstudent on 2005-12-18
[QUOTE=towsonu2003]Not that I don't trust OP's abilities but, I wouldn't use rm as root :) bad stuff happens when you make a typo :-#[/QUOTE]

True. I feel I'm fairly good with puters, but I still make darn good and sure that everything is typed in right before I hit the enter key when I use rm as root.

---

