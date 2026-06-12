---
title: "c,c++ not working in ubuntu10.04"
date: 2010-12-13
forum: Desktop Environments
---

### Post by sharath2k2 on 2010-12-13
the c and c++ are not working in my ubuntu10.04 at all.when i open the file,the #include<stdio.h> and the other stuff are not being displayed in colour.this is disappointing me like anything

---

### Post by 3Miro on 2010-12-13
> **sharath2k2 said:**
> the c and c++ are not working in my ubuntu10.04 at all.when i open the file,the #include<stdio.h> and the other stuff are not being displayed in colour.this is disappointing me like anything

For C and C++ you need a compiler and an editor. What program are you using to open the files? The default should be gedit, however, if you have wine installed you may be using Notepad, which is not a good program. If you right-click on the file, then from properties you can select "open with" and make sure to use gedit. Also, I think gedit wants the files to end in .c or .h or .cpp to be recognized, but I may be wrong.

Gedit is a rather basic program, you can take a look at Geany for more advanced options or Eclipse and Code::Blocks for really advanced editors.

To compile a program, you need to install gcc and g++. Go to System -> Admin -> Synaptic Package manager and you should be able to install them. Find a good tutorial for Linux and C/C++ to tell you how to compile your program (I think Eclipse and Code::Blocks would do it for you).

---

### Post by smo0th on 2010-12-13
does ```
sudo apt-get install g++
``` solve anything?

---

