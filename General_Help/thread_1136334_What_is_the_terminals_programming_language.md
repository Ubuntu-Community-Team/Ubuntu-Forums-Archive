---
title: "What is the terminals programming language?"
date: 2009-04-24
forum: General Help
---

### Post by William24 on 2009-04-24
Ok, so you know in Windows the programming language is batch and to make it execute you can save it in a .bat file. Well, what's the programming language for Ubuntu and what file extension do you save a text file to make it executable in the terminal?

---

### Post by LoneWolfJack on 2009-04-24
you're probably looking for shell script

> sh myscript

or just

> ./myscript

[http://www.freeos.com/guides/lsst/]("http://www.freeos.com/guides/lsst/")

linux doesn't need file extensions. you can add them if you feel like it, but they're just part of the filename. some programs parse the chars behind the last dot though,

---

### Post by William24 on 2009-04-24
Thanks a bunch! =D

---

### Post by CatKiller on 2009-04-25
> **William24 said:**
> what file extension do you save a text file to make it executable in the terminal?

You don't. Text files are executable if their permissions say they are executable.

As to what happens when they're executed, that depends on what sort of script they are, as LoneWolfJack described.

---

### Post by ddrichardson on 2009-04-25
To expand, any text file can be run if you do```
chmod +x scriptname
```What the shell uses to run it is given by what's known as a [shebang]("http://en.wikipedia.org/wiki/Shebang_%28Unix%29"), which must be on the first line:```
#!/bin/sh
```Will make dash run the script whereas```
#!/bin/python
```Will run as a python script.

---

