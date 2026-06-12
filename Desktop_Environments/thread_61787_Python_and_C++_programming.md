---
title: "Python and C++ programming"
date: 2005-09-02
forum: Desktop Environments
---

### Post by craig23 on 2005-09-02
Azz, bored2k, dataw0lf, demon666_nl, FLeiXiuS, jdodson, jdong, kassetra, KiwiNZ, panickedthumb, poofyhairguy and Ubuntu-Geek


I'm studying programming on my own. I've got a limited background of Pascal. I've started to read a little about python and C++.

I have discovered accidentally that I could use the terminal as a Python interpreter just by typing **python**

I've tried using the interpreter by directly coding on the terminal, but I find it more convenient to write a program in gedit and run it in the terminal instead. The ebook I'm reading suggests that if I want to run my file in the interpreter then I just have to write **python filename.py**

But this does not seem to work.

Do I need to save my python codes in a certain folder? Or is there a different command for the Ubuntu terminal to run a python program in the terminal?

One more thing, how could I compile my C++ program (gedit file) through the terminal? What do I have to write? Do I need to save my C++ codes at a certain folder?

---

### Post by npaladin2000 on 2005-09-02
I'm not on your list but I'll answer anyway.  You'd be invoking the GCC compiler for command-line compiling of C++ code.  I don't know how (My pascal knowledge is ancient, but Java works similarly)  but you could do a man gcc (or man g++) or something to get some of the commandline options.

With python (which I'm learning too) it's my understanding that you don't need to type "python" at all, if the source .py file is set up properly, meaning as a shell script using Python as the shell, with the first line being #!/bin/python or something like that (whereas for a vanilla BASH script it would be #!/bin/bash).  You see, theoretically, you could replace the standard (BASH) command-line shell with a Python command-line shell.  I'm considering it, to "encourage" myself to learn the commands, but I'm too used to BASH.

Anyway, I'm pretty sure that's what you need to know...you'd then make your .py file executable with CHMOD 755 (or 7 plus whatever other 2 digits you want to use to set permissions foryour group and all users...do yourself a favor and stick with 755, which is read/write/exec for you, and read/exec for everyone else...744 would be read/no-exec for everyone else and would be another wise choice).  Then you'd just run it like any other program.  Cool, huh?

---

### Post by Shen on 2005-09-02
Typing **python** by itself launches a line-by-line python interpreter; but in the interpreter, you cannot run any terminal commands (such as ls, cd, or python for that matter). You need to exit the python interpreter, by pressing Control-D.

Typing **python filename.py** in a terminal (not in python itself!) will run the file filename.py.

For C++: If your C++ file is called program.cpp, you can compile it by going to the folder that it is in, then type: **g++ program.cpp** in a terminal.

And if it compiles without any errors, it makes a binary file called a.out, which you can run: **./a.out**.

---

### Post by Mike Buksas on 2005-09-04
[QUOTE=craig23]Azz, bored2k, dataw0lf, demon666_nl, FLeiXiuS, jdodson, jdong, kassetra, KiwiNZ, panickedthumb, poofyhairguy and Ubuntu-Geek


I'm studying programming on my own. I've got a limited background of Pascal. I've started to read a little about python and C++.

I have discovered accidentally that I could use the terminal as a Python interpreter just by typing **python**

I've tried using the interpreter by directly coding on the terminal, but I find it more convenient to write a program in gedit and run it in the terminal instead. The ebook I'm reading suggests that if I want to run my file in the interpreter then I just have to write **python filename.py**

But this does not seem to work.

Do I need to save my python codes in a certain folder? Or is there a different command for the Ubuntu terminal to run a python program in the terminal?

One more thing, how could I compile my C++ program (gedit file) through the terminal? What do I have to write? Do I need to save my C++ codes at a certain folder?[/QUOTE]


Not on your list, but I'll try and help anyway.

The python intrepreter will look in the current directory when you use it to run a script. e.g. **python filename.py** will only work if you can see **filename.py** when you type ls. Or, you can give the full path of the file, e.g. **python ~/code/python/filename.py**.

To compile c++ code, the first choice for compilers is g++, the GNU C++ compiler. It is part of a very complete set of compilers for C/C++/Fortran etc... To use it, install **build-essential**:

```
sudo apt-get install build-essential
```

You will then run gcc from the command line, usually as follows:

```
gcc myfile.cc -o myfile
```

This will compile the code in myfile.cc and output an executable *myfile*

Hope this helps.

---

