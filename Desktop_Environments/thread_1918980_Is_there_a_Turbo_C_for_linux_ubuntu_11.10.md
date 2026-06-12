---
title: "Is there a Turbo C for linux ubuntu 11.10?"
date: 2012-02-02
forum: Desktop Environments
---

### Post by shreyas_patel21 on 2012-02-02
Hi all

is there any program like turbo C in ubuntu 11.10 in which we can compile and run C code?

---

### Post by TheFu on 2012-02-02
gcc is the C compiler.
If you want a lite IDE, I can recommend Geany, but lots of C programmers use vi or emacs too.

Back when I was a professional C/C++ dev, we generally use an editor, like vi, a separate debugger, gdb, and a separate build tool - called "make".

I'm fairly certain there are turbo-C like IDEs available, but they will make calls to the external tools - make, gdb, gcc.
I'd search here [http://freecode.com/search?q=IDE&submit=Search](http://freecode.com/search?q=IDE&submit=Search)  to find lots of IDE options.

---

### Post by shashankvatedka on 2012-02-02
Hi,

Linux has a built in C compiler and you don't need any additional software. Lets say you want to create a program called filename.c. 
Just open a terminal and type 

user-desktop:~$ gedit filename.c

The editor opens wherein you can type your program. After saving the file, go back to the terminal to compile your file. Use

user-desktop:~$ gcc -o filename filename.c

To run the file just use

shashank@smart-desktop:~$ ./filename

Instead of gcc, you can also use

shashank@smart-desktop:~$ cc filename.c

To run the file, type

shashank@smart-desktop:~$ ./a.out

Hope this helps! :D

---

### Post by shreyas_patel21 on 2012-02-04
thank you shashank..

I compiled it successfully but i am not able to run it

should  I write $ ./hello.c to run hello.c?

---

### Post by shreyas_patel21 on 2012-02-04
thank you again I run it successfully.

---

### Post by sherlock007 on 2012-11-04
can any one help me on this problem.... When i run the exe file, a pop up message for me is .. Here is the message below...   


"The version of this file is not compatible with the version of Windows you're running. Check your computer's system information to see whether you need an x86 (32-bit) or x64 (64-bit) version of the program, and then contact the software publisher. "

---

### Post by Impavidus on 2012-11-04
First of all you should have started a new thread in the progammer talk subforum instead of adding a reply to this thread.

Next, do I understand correctly that you compiled a program using ubuntu, named it a .exe and then tried to run it on windows? That won't work, the system requires a different format. You will need a cross compiler.

---

### Post by shailendra kumar on 2012-11-07
> **shashankvatedka said:**
> Hi,

Linux has a built in C compiler and you don't need any additional software. Lets say you want to create a program called filename.c. 
Just open a terminal and type 

user-desktop:~$ gedit filename.c

The editor opens wherein you can type your program. After saving the file, go back to the terminal to compile your file. Use

user-desktop:~$ gcc -o filename filename.c

To run the file just use

shashank@smart-desktop:~$ ./filename

Instead of gcc, you can also use

shashank@smart-desktop:~$ cc filename.c

To run the file, type

shashank@smart-desktop:~$ ./a.out

Hope this helps! :D

Dear Friend,
From where I open terminal, since I am new to UBUNTU. Can you suggest me!

---

