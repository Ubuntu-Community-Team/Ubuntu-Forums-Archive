---
title: "Program to search/edit variables in RAM (a memory editor)"
date: 2008-12-23
forum: General Help
---

### Post by crazyfuturamanoob on 2008-12-23
I wan't to cheat in games and I need a memory editor. Maybe there's one for Ubuntu? Thanks. :D

---

### Post by Titan8990 on 2008-12-23
Usually PC games have built-in functions for cheating.


If you are talking about cheating in games that are played online competitively, then you shouldn't be cheating.

---

### Post by roelpeeters on 2008-12-23
Unless you have the source code, the relation between 'meaningful variablename' and memory location at runtime is completely random and up to the compiler and/or runtime environment (kernel paging, linker, program loader,etc). 
<old geek talk>When I was young, we used to use the debugger to follow the flow of the program to find out where and how memory locations that looked interesting were modified. Based on this info, we would write a patch. </old geek talk>
Tools like gdb, nm and od would be a good start.

---

### Post by crazyfuturamanoob on 2008-12-23
Ok I got the source code of the game, and it's not your business if I cheat an online game.

So I should write some like "patch" for the game, to edit some important variables (score, position, inventory)?

I know C and Python, but how to write it or where to start from? What does debugger help, can't I see the variable names & values from source code?


Edit: I'm trying to learn using gdb, and now I'm wondering, how to change variables of the program with gdb at breakpoints?

---

### Post by roelpeeters on 2008-12-24
You would have to modify the original source code, and recompile the source into the executable. Since you have the source code, I imagine you also have a makefile or some sort of building software (like make, scons, etc). This build allows you to automatically compile and link the source code into the executable.

In order to get started on gdb I can recommend the following link to the manual of gdb:
[http://sourceware.org/gdb/current/onlinedocs/gdb_toc.html]("http://sourceware.org/gdb/current/onlinedocs/gdb_toc.html")

---

### Post by crazyfuturamanoob on 2008-12-24
Maybe I could compile the program with -g option to make it gdb compatible, and then use gdb as the memory editor, like editing variables with gdb? 

Only problem is that I don't know the names of the variables, can gdb search for values? I just learned how to edit variables by names/addresses.

And the source code is so long (thousands of lines in lots of files) I can't edit the source code efficiently. It's impossible to find the variable declarations.

---

### Post by roelpeeters on 2008-12-24
Unfortunately that is the only way - try to understand the source code to see what it is doing before you can modify it. 
You have to compile the source code with -g in order to be able to debug it with gdb. Gdb can set breakpoints that stop only when certain variables have certain values, but for that you need to know which variables to inspect. Searching a certain memory space for a certain value is very unreliable even if you think you know the value it should be. It depends on the program, processor and linker on how the value is stored in memory - this could be as an int, double or string; each of which have their own encoding in bytes in memory. You probably learn more from reading the source code to understand how the values you are looking for are calculated and stored. Then you can write a fix/patch that will allow you to change the variables.

---

