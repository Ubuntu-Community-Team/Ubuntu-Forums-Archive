---
title: "Code Blocks , permission denied"
date: 2009-05-24
forum: General Help
---

### Post by sudoomar on 2009-05-24
hello
i want to use a  C compiler on Ubunut

i installed Code Blocks..

i wrote a hello world program to test it..

when i want to Run the program i get an Erorr saying permission denied

please help

---

### Post by x33a on 2009-05-24
you'll have to enable the exec flag in your fstab.

post the output of
```
cat /etc/fstab
```

---

### Post by sudoomar on 2009-05-24
> **x33a said:**
> you'll have to enable the exec flag in your fstab.

post the output of
```
cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=06a4082c-f0f6-4488-ac42-9718e0d04f88 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=217af2e7-e5f0-49d3-a621-66eb2b44bf45 /storage        ext2    relatime        0       2
# /dev/sda6
UUID=7bae1de2-6ce9-4e08-a940-ae66d6ef86b4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
omar@omar-laptop:~$

---

### Post by x33a on 2009-05-24
```
gksudo gedit /etc/fstab
```put exec next to relatime, like this:

> # /dev/sda5
UUID=217af2e7-e5f0-49d3-a621-66eb2b44bf45 /storage        ext2    relatime,exec        0       2

ps: first unmount that partition.

---

### Post by sudoomar on 2009-05-24
> **x33a said:**
> ```
gksudo gedit /etc/fstab
```put exec next to relatime, like this:



ps: first unmount that partition.

well i do not think this is the problem

i am not using the storage partition

i got a screen with sh :/ home/omar/Untiteled1: Permission denied

press enter to continue

my source file is Untiteled1

---

### Post by x33a on 2009-05-24
post the output of 
```
ls -l
```
for that file.

---

### Post by sudoomar on 2009-05-24
> **x33a said:**
> post the output of 
```
ls -l
```
for that file.

-rwxr-xr-x 1 omar omar   56 2009-05-24 15:54 Untitled1

---

### Post by sudoomar on 2009-05-24
> **sudoomar said:**
> -rwxr-xr-x 1 omar omar   56 2009-05-24 15:54 Untitled1

how can i solve this problem?

---

