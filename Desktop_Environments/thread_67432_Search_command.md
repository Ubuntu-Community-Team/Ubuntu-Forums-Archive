---
title: "Search command"
date: 2005-09-20
forum: Desktop Environments
---

### Post by ones on 2005-09-20
I would like to know a command to find easyly files or folders through the console

---

### Post by SGC on 2005-09-20
Fast, but not up to date:
```
locate FILE_NAME
```
Slow, but find every thing:
```
find ~ -name FILE_NAME
```
change ~ to the directory where you want to perform the search [~ will searchs your home directory]

---

### Post by frodon on 2005-09-20
[QUOTE=SGC]Fast, but not up to date[/QUOTE]Why do you say "not up to date" ? The **locate** function search a file within a database, to update this database : ```
sudo updatedb
```
So, i think the easiest way to search a file is to use the **locate** function but if you're looking for a recent file or if you use the locate function for the first time think to run a **sudo updatedb** before.

enjoy  ;-)

---

### Post by SGC on 2005-09-20
[QUOTE=frodon]Why do you say "not up to date" ? The **locate** function search a file within a database, to update this database : ```
sudo updatedb
```
So, i think the easiest way to search a file is to use the **locate** function but if you're looking for a recent file or if you use the locate function for the first time think to run a **sudo updatedb** before.

enjoy  ;-)[/QUOTE]
 But its not convenience  to update the database each time you want to make a search for a new file since the update is takes some time.

---

### Post by ones on 2005-09-20
The command it's basically for help me to know where things are installed and in this way manage the configuration file that most programs have. 

I think I used to use other command different than find and locate, but I can't remember wich one  ](*,)

Thx anyway, I will try those commands

---

### Post by bsussman on 2005-09-20
This is going to degenerate quickly into a 'stupid commandline tricks':grin: thread but:

If you know approximately where it is:

 ```
> cd 'topdirectoryofwhereyouthinkitis'
> ls -latR|grep 'whatyerlookingfor'|less
```

might be good...

the R for recursive is key here.....

---

### Post by frodon on 2005-09-20
[QUOTE=SGC]But its not convenience  to update the database each time you want to make a search for a new file since the update is takes some time.[/QUOTE]That's why [crontab](http://www.adminschoice.com/docs/crontab.htm) exist !

---

