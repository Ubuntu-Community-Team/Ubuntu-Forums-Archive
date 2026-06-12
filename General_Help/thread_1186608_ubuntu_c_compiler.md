---
title: "ubuntu c compiler"
date: 2009-06-13
forum: General Help
---

### Post by suffery on 2009-06-13
hey guys i just got ubuntu today and i absolutely love it
im 15 and i mtrying to find a a compiler
my dad said cygwin was good but i couldent figure it out..
im trying to learn c programming
then i heard about gnu but couldent find a download for it or even how to download it

is there any good compilers for ubuntu?
thanks

---

### Post by Amilo1718 on 2009-06-13
first of all: welcome
second: what do you want to compile?

---

### Post by suffery on 2009-06-13
c and c++

im trying to learn c programming

---

### Post by joyneo04 on 2009-06-13
hey welcome to ubuntu...try gcc..for details u can check out google...

---

### Post by joyneo04 on 2009-06-13
check this two link....
[http://gcc.gnu.org/](http://gcc.gnu.org/)
[http://www.delorie.com/gnu/docs/gcc/gcc_toc.html](http://www.delorie.com/gnu/docs/gcc/gcc_toc.html)....

---

### Post by trecool999 on 2009-06-13
You'll want to download "gcc" and "g++" from Synaptic Package Manager.
To compile a program, in the terminal do:
```
gcc file.c program
./program
```
For C and:
```
g++ file.c program
./program
```
For C++.

---

### Post by suffery on 2009-06-14
i have gcc and g++
i made a c program in nano and saved it (ctrl -o)
its in my home folder

it gave me no directory found

where do i put the file?

also the file name is 02L0.c
its a text file.

im guessing i have to put it in a folder somewhere?

if so where?

---

### Post by suffery on 2009-06-14
sorry i really need a answer
bump

---

### Post by TrakerJon on 2009-06-14
You'll like this one...

Geany is a fast and lightweight IDE for programming in various languages.
**sudo apt-get install geany**

Make sure you have this installed...

If you program in C\C++ languages you&#8217;ll need the Build-Essential packages.
**sudo apt-get install build-essential**

---

### Post by ActiveFrost on 2009-06-14
Let's say you've saved your .c file ( named myapp.c ) into your home directory.

Terminal :
```
cd $HOME
gcc myapp.c -o MyApp
```

---

### Post by suffery on 2009-06-14
ok i got it
but now how do i open the file and execute it
clicking doesent do anything

---

### Post by ActiveFrost on 2009-06-14
```
./application_name
```

---

### Post by suffery on 2009-06-14
john@ubuntu:~$ ./02L01.c
bash: ./02L01.c: Permission denied

ok why is it denieing me permission im the admin

---

### Post by ActiveFrost on 2009-06-14
> **suffery said:**
> john@ubuntu:~$ ./02L01.c
bash: ./02L01.c: Permission denied

ok why is it denieing me permission im the admin

Because you are trying to launch your source file, not your application !
02L01.c is your source file, not executable.
Do this :
```
gcc 02L01.c -o MyApp
./MyApp
```

---

### Post by suffery on 2009-06-14
john@ubuntu:~$ gcc 02L01.c -o MyApp
john@ubuntu:~$ ./MyApp
howdy, neighbor| This is my first c program.


thanks so much you guys have helped me out a ton

---

