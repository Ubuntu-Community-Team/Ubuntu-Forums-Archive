---
title: "What is a good  C++ compiler that works with Ubuntu 8.04"
date: 2009-03-18
forum: General Help
---

### Post by dago1 on 2009-03-18
I can't find any c++ compilers at all please help.

---

### Post by taurus on 2009-03-18
Have you installed the build-essential package?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by dago1 on 2009-03-18
Ok taurus I put those codes in the terminal something was downloaded now what?

---

### Post by taurus on 2009-03-18
```
c++
```
It will give you an error message because you didn't include an input file.  In other words, you would run

```
c++ filename
-or-
g++ filename
```

---

### Post by dago1 on 2009-03-18
here is what I get when i write c++ filename

dago@dago-desktop:~$ c++ filename
c++: filename: No such file or directory
c++: no input files
dago@dago-desktop:~$

---

### Post by taurus on 2009-03-18
You're supposed to replace _filename_ with your C program.  If you wrote a program called testing.cpp, then you would run it as, assuming you are in the same directory where testing.cpp is

```
g++ testing.cpp
```

---

### Post by dago1 on 2009-03-18
I don't have a C program, I want a c/c++ compiler so I can learn programing.

---

### Post by taurus on 2009-03-18
Now you have one, gcc.  At this point, you just need to write a C program and then compile it.  Until then, there is nothing much you can do.

```
gcc -v
```

---

### Post by dago1 on 2009-03-18
ok how do i open gcc?

---

### Post by taurus on 2009-03-18
You cannot open gcc; it is a compiler.  You need to write a C program first and then use gcc to compile that program that you wrote.

Perhaps a good C programming book is what you need.

---

### Post by mb_webguy on 2009-03-18
I think you're talking about an IDE (like Visual C++ for Windows), which is something else entirely.

First of all, you don't need an IDE to learn C++ (or any other language).  All you really need are a text editor (e.g. gedit, kate, nano) and either a compiler (for compiled languages) or an interpreter (for scripting languages).  The most commonly used compiler for C++ in Linux is g++.

An IDE simply provides a graphical environment and a number of tools to help create programs.  Any C++ IDE for Linux will probably use the g++ compiler.  A number of IDEs are available for a number of languages.  For C++, you could try Code::Blocks, MonoDevelop, KDevelop, or NetBeans.  All of these are in the Ubuntu repositories.  I suggest the full version of NetBeans from the [official website]("http://www.netbeans.org/downloads/index.html"), as it supports a number of different languages.

If you don't have any prior experience with programming, however, I'd suggest you start with something like Python instead of C++.  You should focus more on learning to program than learning a specific language.  Once you know the concepts of programming, learning a new language is just a matter of learning the differences in syntax.  

Python is a good language to start with because it's a high-level language, which means you don't have to worry about low-level concepts like garbage collection.  It's also a scripting language, so you can see the results of changes in the code instantly, without wasting a lot of time recompiling.

---

