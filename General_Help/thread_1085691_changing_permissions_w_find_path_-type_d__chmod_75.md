---
title: "changing permissions w/ find path -type d | chmod 755 won't handle spaces"
date: 2009-03-03
forum: General Help
---

### Post by jimsamson on 2009-03-03
i am trying to change the permissions of all directories in a path, but the command i am using will not handle spaces in the directory name, any ideas how to fix this (without removing the spaces from the directory names) ... the command i am currently using is find path/ -type d | chmod 755

---

### Post by heindsight on 2009-03-03
find allows you to run a command for each file it finds, by using the -exec action. Use it like:

```
find PATH TESTS -exec COMMAND ;
```

For example:
```
find . -type d -exec chmod 755 \{\} \;
```
Each -exec command should be terminated by a ; (the \ is there to prevent the shell from interpreting the ; as a command separator). In each -exec command, {} will be replaced with the name of the file find is currently processing (again the \'s are there to prevent the shell from interpreting the {}). See the find manual for more details:
```
man find
```

---

### Post by DGortze380 on 2009-03-03
> **jimsamson said:**
> i am trying to change the permissions of all directories in a path, but the command i am using will not handle spaces in the directory name, any ideas how to fix this (without removing the spaces from the directory names) ... the command i am currently using is find path/ -type d | chmod 755

UNIX doesn't like spaces.
Get in the habit of not using them.

Use and Under Score or Capital Letters to Delineate.

my_Directory
myDirectory

when typing a PATH with a space in a directory name, auto-complete is easiest, or use the escape character.

/Path/To/my[tab]
/Path/To/my\ directory

---

