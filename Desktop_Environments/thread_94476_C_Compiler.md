---
title: "C Compiler"
date: 2005-11-24
forum: Desktop Environments
---

### Post by derm0 on 2005-11-24
Hi all,
I've only just recently started with Ubuntu and was wondering if there was a way to compile c files in the shell script. The standard Unix cc comand doesn't seem to work. Does anyone know if Ubuntu does have a c compiler & if it does what the shell command is to run it??

Thanks,
Derm

---

### Post by f1dave on 2005-11-24
It surely does.

gcc is your man.

---

### Post by maulattu on 2005-11-24
you should download it:
```
sudo apt-get update
sudo apt-get install gcc
sudo apt-get install gdb
```

gcc is the compiler, while gdb is the debugger ;)

---

### Post by David Marrs on 2005-11-24
cc should be aliased againsed gcc, but you need to install it first. apt-get install build-essentials will give you the standard libraries and make utilities as well.

---

### Post by maulattu on 2005-11-24
[QUOTE=David Marrs]apt-get install build-essentials[/QUOTE]

yes, sure! try this one and you shouldn't have any problem:cool:

---

