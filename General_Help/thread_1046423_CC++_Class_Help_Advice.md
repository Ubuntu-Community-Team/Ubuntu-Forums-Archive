---
title: "C/C++ Class Help/ Advice"
date: 2009-01-21
forum: General Help
---

### Post by yosef on 2009-01-21
I am starting a C/C++ programming class, the prof has recommended everyone use microsoft visual C++ which comes with the book.  I don't wanna.  I am running Ubuntu Netbook Remix on a Sylvania G Meso.  What should I install in place of micro visual C++?

---

### Post by StOoZ on 2009-01-21
Netbeans ?
eclipse?

---

### Post by namegame on 2009-01-21
I would recommend you look over in the Programming Talk subforum.

As for your question, the absolute minimum requirements to program in C/C++ in Ubuntu are the "build-essential" package and a text editor (vi, gedit, nano, whatever).

You'll want:

```
sudo apt-get install build-essential
```

To compile a C++ source file:
(in the same directory as your file)

```
g++ NameOfFile.cpp
```

You'll then be able to run your program with the following command:

```
./a.out
```

Remember, this is the bare MINIMUM required for C++ programming. As I said you'll find much more detailed information here:

[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

Read the stickies as well.

---

### Post by yosef on 2009-01-28
Thank you very much, I really appreciate your help.

---

