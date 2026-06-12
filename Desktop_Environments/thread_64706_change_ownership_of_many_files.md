---
title: "change ownership of many files"
date: 2005-09-11
forum: Desktop Environments
---

### Post by flightcrank on 2005-09-11
how can i select a group of many files (over 100) and change ownership of them.

i know i can do 

```
sudo chown user:group filename.ext
```

but thats only for one file, is the a program that will let you select many files to do this task ?

---

### Post by codejunkie on 2005-09-11
[QUOTE=flightcrank]how can i select a group of many files (over 100) and change ownership of them.

i know i can do 

```
sudo chown user:group filename.ext
```

but thats only for one file, is the a program that will let you select many files to do this task ?[/QUOTE]
put them in a folder and then ```
sudo chown user:group nameoffolder -R
```

---

### Post by flightcrank on 2005-09-11
whoa that saved me hours !, thanks

---

