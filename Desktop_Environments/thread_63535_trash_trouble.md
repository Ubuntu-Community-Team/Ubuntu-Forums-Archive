---
title: "trash trouble"
date: 2005-09-08
forum: Desktop Environments
---

### Post by nickless on 2005-09-08
Every time I delete something completely ( I usually do by emptying the trash) I don't get back the space it used...
```
jan@meanmachine:~ $ df -h
Dateisystem          Größe Benut  Verf Ben% Eingehängt auf
/dev/hdc1              13G  7,7G  4,3G  65% /
tmpfs                 253M     0  253M   0% /dev/shm
/dev/hdb1              56G   53G  195M 100% /home/jan
/dev/hda1              37G   32G  4,8G  87% /home/jan/windoof
/dev                   13G  7,7G  4,3G  65% /.dev
none                  5,0M  2,8M  2,3M  56% /dev

```
hdb1 is the problem here... also I find it strange that I have a .Trash-1000 and a .Trash-root in my home folder. :-| 
What is going on?

---

