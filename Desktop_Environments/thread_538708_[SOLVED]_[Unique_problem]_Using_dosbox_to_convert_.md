---
title: "[SOLVED] [Unique problem] Using dosbox to convert .txt to .pdb"
date: 2007-08-30
forum: Desktop Environments
---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-08-30
I've googled this issue extensively and, as far as Linux is concerned, this issue is fairly unique, so it's going to take some explaining.

I use a program for my PDA called SuperMemo, which is a flashcard program. You can use a program called smconv.exe to convert .txt files, assuming they are formatted correctly, to .pdb files, which is the SuperMemo format.

I've gotten dosbox to convert the .txts to .pdb. However, they do not convert correctly. According to a Mac user who had a similar problem ( [http://www.reavesmd.com/blog/2006/05/24/smconv_mac/](http://www.reavesmd.com/blog/2006/05/24/smconv_mac/) ), this is probably because of formatting issues.

**I need someone in particular who understands both Mac and Linux well enough to make sense of that article and tell me what I need to do to fix the text file formatting issues for Ubuntu.**

If it helps, on Windows you would structure your .txt files like this before converting:

Q: question1
A: answer1

Q: question2
A: answer2

I use (or will use) this program for school, as it is a much more effective way of making flash cards than physically drawing them. Help is greatly appreciated.

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-08-31
bump

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-09-01
bump

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-09-01
bump

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-09-01
bump

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-09-01
bump

---

### Post by yabbadabbadont on 2007-09-01
Sounds like you need to install the tofrodos package.
```
/home/daffy $ aptitude show tofrodos 
Package: tofrodos
State: installed
Automatically installed: no
Version: 1.7.6-2
Priority: optional
Section: utils
Maintainer: Florian Ernst <florian@debian.org>
Uncompressed Size: 69.6k
Depends: libc6 (>= 2.4-1)
Conflicts: sysutils (<= 2.0.0-1)
Description: Converts DOS <-> Unix text files, alias tofromdos
 DOS text files traditionally have CR/LF (carriage return/line feed) pairs as their new line delimiters while Unix text files
 traditionally have LFs (line feeds) to terminate each line. 
 
 Tofrodos comprises one program, "fromdos" alias "todos", which converts text files to and from these formats. Use "fromdos" to
 convert DOS text files to the Unix format, and "todos" to convert Unix text files to the DOS format. 
 
 This functionality is also available via the dos2unix/unix2dos symlinks. 
 
 Homepage: http://www.thefreecountry.com/tofrodos/index.shtml

```
Create your text files in linux.  Open a terminal window and use "todos NameOfFileToBeConverted" to change the line ends to the DOS format.  Then you can use the exe utility they provide, by running it inside of DosBox, to convert your txt file to pdb format.

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-09-01
[SIZE="6"]***It works!***[/SIZE]

Thank you!! :-D

---

### Post by yabbadabbadont on 2007-09-01
You are welcome.  I figured it was something like that.  You pick these things up when you've been using Linux for 11 years.  ;)

---

