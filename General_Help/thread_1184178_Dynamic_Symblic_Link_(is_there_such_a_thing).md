---
title: "Dynamic Symblic Link (is there such a thing?)"
date: 2009-06-10
forum: General Help
---

### Post by beattyml1 on 2009-06-10
I am wondering is there a way to define a symbolic link in such a way that its target path is determined by what folder. For example:

file img.jpg in /home/user
create a link lnk.jpg the file /home/user/img.jpg also in /home/user
I then copy lnk.jpg to a new folder /home/user2/something which also contains a file called img.jpg
the lnk.jpg in /home/user2/something now points to the img.jpg in /home/user2/something

---

### Post by justin_guerin on 2009-06-10
If I understand your question correctly, the answer is yes:

```
justin@work-laptop:~$ mkdir -p a/b/
justin@work-laptop:~$ cd a
justin@work-laptop:~/a$ touch foo.txt
justin@work-laptop:~/a$ touch b/foo.txt
justin@work-laptop:~/a$ ln -s ./foo.txt bar.lnk
justin@work-laptop:~/a$ ls -l
total 4
drwxr-xr-x 2 justin justin 4096 2009-06-10 22:11 b
lrwxrwxrwx 1 justin justin    9 2009-06-10 22:11 bar.lnk -> ./foo.txt
-rw-r--r-- 1 justin justin    0 2009-06-10 22:11 foo.txt
justin@work-laptop:~/a$ cp -d bar.lnk b/
justin@work-laptop:~/a$ ls -l b
total 0
lrwxrwxrwx 1 justin justin 9 2009-06-10 22:12 bar.lnk -> ./foo.txt
-rw-r--r-- 1 justin justin 0 2009-06-10 22:11 foo.txt
justin@work-laptop:~/a$

```

The important point is the -d in the cp command:
       -d     same as --no-dereference --preserve=links

---

