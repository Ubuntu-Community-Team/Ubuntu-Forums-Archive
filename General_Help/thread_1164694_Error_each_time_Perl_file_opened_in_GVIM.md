---
title: "Error each time Perl file opened in GVIM"
date: 2009-05-19
forum: General Help
---

### Post by jonathansizz on 2009-05-19
I have recently started learning Perl programming, I am using GVIM as my editor.

Initially I didn't have any problems, but since I have reinstalled my operating system I get the following error every time I try to open a .pl file:

> Can't call method "process" on an undefined value at (eval 28) line 3.

The number following eval (i.e. 28 in this example) seems to be incrementing each time I try to open a file.

I can press Enter to continue, but obviously I'd rather know what's causing the problem and fix it.

I would appreciate any help on this.

---

### Post by space_agent on 2011-02-21
I had a very similar problem:
```
Can't call method "process" on an undefined value at (eval 14) line 5.
```
Upon closing and reopening vim it gave an error about Perl::Tags missing so I installed it with
```
sudo -H cpan
install Perl::Tags
```
and now the error is gone !

---

### Post by fungiblename on 2011-03-10
@space_agent: Thanks! Worked perfectly for me!

---

