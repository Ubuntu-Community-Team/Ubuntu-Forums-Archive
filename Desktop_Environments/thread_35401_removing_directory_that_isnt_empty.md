---
title: "removing directory that isnt empty?"
date: 2005-05-18
forum: Desktop Environments
---

### Post by drswete on 2005-05-18
hi i am new to linux and i would like to as this question.

how do u remove a directory that isnt empty?

im not sure if this question belongs here but i didnt really know where else to put it.  thanks in advance for helping

---

### Post by bruizer on 2005-05-18
Try "rm -r".

---

### Post by sfw5000 on 2005-05-18
might want to make that... 

rm -rf 

please be careful when using this command with sudo or as root... it won't ask for confirmation, one little typo and you could be cery sorry...

---

### Post by bruizer on 2005-05-18
If using the -f yes, as this forces the deletion without prompting... Good Point!

---

### Post by Sam on 2005-05-18
If you are not sure you can also use
```
$ rm -rfi <dir>
```This will ask a confirmation for each file.

---

### Post by sfw5000 on 2005-05-18
Yeah -- I only recommend the -f switch because if you are removing a directory with a lot of files having to confirm each one is a pretty big in the butt

---

### Post by Xian on 2005-05-18
[QUOTE=Sam]If you are not sure you can also use
```
$ rm -rfi <dir>
```This will ask a confirmation for each file.[/QUOTE]
That or similar type of variation is the best. It is just too easy to make an oops otherwise.

---

### Post by drswete on 2005-05-18
thx a lot guys

---

