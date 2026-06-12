---
title: "How to run C and C++ applications?"
date: 2008-11-12
forum: Delhi Team
---

### Post by Abhishek Sinha19850130 on 2008-11-12
I would like to run these applications on my Ubuntu. I use hardy heron. Is there a specific compiler for it. 

Looking forward to responses.

---

### Post by prshah on 2008-11-12
> **Abhishek Sinha19850130 said:**
> I would like to run these applications on my Ubuntu. I use hardy heron. Is there a specific compiler for it. 

You don't need a compiler to _run_ applications; they will run just fine as native binary apps.

That said, if you want to write your own programs and then compile them, you can use g++, the c / c++ compiler included with your Ubuntu distribution.

---

### Post by Abhishek Sinha19850130 on 2009-03-19
HEllo PRShah,

I am really sorry for this late reply. Thanks for your reply. But how should i start programming in C, write programs, compile them and see them in the output? DO i have to use terminal for it. Usuall for windows we start in borland!!

---

### Post by luckydeveloper on 2009-04-30
If you want to do C/C++  programming, 

1. you need to type your programs in an editor such as emacs, vim etc
2. And then compile them using a compiler

To install a compiler,go to terminal and type 
sudo apt-get install build-essential

To install emacs, go to terminal and type
sudo apt-get install emacs22

After these are over, go to terminal, start emacs, type your program in it and compile using the command 
gcc <filename.c>
and then type
./a.out
to run your program...

For more, refer [https://help.ubuntu.com/8.04/programming/C/index.html](https://help.ubuntu.com/8.04/programming/C/index.html)

---

### Post by Kushal Sejwal on 2009-05-05
The first thing is to install compilers as pointed out in last post, simply fire the following command in the terminal:
```
sudo apt-get install build-essential
```

Now instead of using commands each time to compile, build and run. You simply install an IDE(Borland/TC in windows) like Geany to do the stuff for you.
```
sudo apt-get install geany
```

---

### Post by firen on 2009-08-02
If using terminal haunts you, use gedit ( Applications > Accessories> Text Editor ) it has all good syntax highlighting and stuff for programmers. If you want to keep yourself completely away from terminal, try IDEs such as KDevelop, for Gnome look at Anjuta.

---

### Post by mrman208 on 2010-03-29
> **firen said:**
> If using terminal haunts you, use gedit ( Applications > Accessories> Text Editor ) it has all good syntax highlighting and stuff for programmers. If you want to keep yourself completely away from terminal, try IDEs such as KDevelop, for Gnome look at Anjuta.

I would suggest using the Eclipse IDE with CDT for C/C++ development, but you can use whatever you want.

---

### Post by toji on 2010-07-13
Hey you should also try code blocks IDE.
but i really think you should use vim. once you get a hang of the command line it's really fun!!

---

### Post by shyguy1188 on 2010-08-18
try writing your code in GEDIT(application->accessories->gedit)....

write your code there.. save it....

open TERMINAL(application->accessories->terminal)

commands are:=>

gcc -v <your file name>.<c>


use g++ instead of gcc for <c++> programs. u'll get errors with the line no written beside them... it's really easy and fun.. 

you can also find the help by typing 

man gcc    in terminal. ;)

---

### Post by tushar maroo on 2011-03-11
if you are at a very basic step then i recommend you to go for gcc(for C) and g++(for C++)
type in terminal:-
command line for** compiling c-program**:
**gcc filename.c**
then for **run** it type:-
**./a.out**

similarly for cpp programs
**g++  filename.cpp**
and then for running
**./a.out**

---

