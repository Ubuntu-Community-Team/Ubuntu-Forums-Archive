---
title: "permissions"
date: 2005-05-22
forum: Desktop Environments
---

### Post by Infernal on 2005-05-22
is it possible to change all the permissions into 775 in one time.i mean that if i chmod   1 ddirectory, all files and subdirectories all changed too


thx

---

### Post by Sam on 2005-05-22
> [Please do not post questions here. This is for HOWTO's and FAQs only](http://ubuntuforums.org/showthread.php?t=22348)


To chmod every file in directory and subdirectories
```
$ find . -type f -exec chmod 775 {} \;
```
To chmod every subdirectories in directory
```
$ find . -type d -exec chmod 775 {} \;
```
To chmod everything
```
$ chmod -R 775 *
```

---

### Post by Infernal on 2005-05-22
[QUOTE=Sam]To chmod every file in directory and subdirectories
```
$ find . -type f -exec chmod 775 {} \;
```
To chmod every subdirectories in directory
```
$ find . -type d -exec chmod 775 {} \;
```
To chmod everything
```
$ chmod -R 775 *
```[/QUOTE]
 
bash: syntax error near unexpected token ('

and the last command won't work, every file and folder insn't changed  :-?

---

### Post by Sam on 2005-05-22
[QUOTE=Infernal]bash: syntax error near unexpected token ('

and the last command won't work, every file and folder insn't changed  :-?[/QUOTE]
It's not (), but {}

The last command works well on my box, that's strange...

---

