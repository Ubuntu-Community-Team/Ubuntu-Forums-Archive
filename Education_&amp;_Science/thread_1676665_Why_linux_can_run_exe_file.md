---
title: "Why linux can run exe file"
date: 2011-01-27
forum: Education &amp; Science
---

### Post by new7linux on 2011-01-27
Why Linux can **NOT** run EXE file??

I know that we can run EXE file by using Wine program.

as i understand:
EXE file commnly   is an object code"machine language" that the CPU can understand it directly,,

THE operating system is load this EXE file from hard disk (or any media) to RAM ,
and the CPU directly execute it from the memory,,

So why Linux not directly load this EXE file to RAM 
and then then the CPU?????

---

### Post by Simian Man on 2011-01-27
> **new7linux said:**
> EXE file commnly   is an object code"machine language" that the CPU can understand it directly,,

That's not strictly true.  Exe files do contain object code, but it is still dependent on the operating system to do certain things when loading the program into memory.  First off Windows uses the "PE" format for object code (ironically the P stands for portable).  Linux now uses the Elf format, it used to use one called Coff.

Apart from format differences, there is also the fact that executable also rely on libraries and system calls to be installed that are very different between Linux and Windows.  Also the way libraries are loaded are different between systems.

So exe files are actually OS and CPU dependent.

---

### Post by Kirboosy on 2011-01-27
Because exe wasn't designed for Linux. [Wikipedia]("http://en.wikipedia.org/wiki/EXE")

Its like trying to run a deb file in Windows. Since it wasn't designed to run in Windows it won't work properly.

---

### Post by new7linux on 2011-01-27
> **Simian Man said:**
> That's not strictly true.  Exe files do contain object code, but it is still dependent on the operating system to do certain things when loading the program into memory.  

first thank you for reply.

if i was write in c++ to make exe file::-
```
cout<<"hello word
``` 
then the compiler will  make the machine language and store it in the hard.

then this simple program it just need to load from hard disk to memory ,

 what OS make to this file except loaded it to the memory??

---

### Post by Simian Man on 2011-01-27
Try compiling a simple program and open up the output in a text editor.  You will see that there are readable references to libraries, system calls, strings, data and lots of other stuff besides just the object code making up your program.  These "other things" are done very differently on different systems.

Basically it's not as simple as you are supposing :).

---

### Post by new7linux on 2011-01-27
> **Simian Man said:**
> Try compiling a simple program and open up the output in a text editor.  You will see that there are readable references to libraries, system calls, strings, data and lots of other stuff besides just the object code making up your program.  These "other things" are done very differently on different systems.



Ok i understanding you .

can you give some example"or link"  to learn about  **These "other things"..**

---

### Post by Bölvaður on 2011-01-27
You can read about how Wine works.
Or you can write your own operating system, you'll learn a lot of it if you have enough time and discipline to actually go through with it. You will gain a lot from going through the sourecode from old operating systems that have opened up their code.

---

### Post by bouncingwilf on 2011-01-27
Another way of looking at it is that since Win 95 (using microsoft OS's) user software has no direct interaction with the hardware rather the software makes calls to the operating system which in turn controls the hardware. i.e. there's a proprietary layer between you and the machine.

Bouncingwilf

---

