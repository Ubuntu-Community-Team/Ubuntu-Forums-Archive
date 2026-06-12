---
title: "[SOLVED]GCC Problems"
date: 2009-05-08
forum: General Help
---

### Post by etheodos on 2009-05-08
Hey,

This may seem like a very dumb question, but I have C code that I would like to compile and run and I was wondering exactly how I would do that.  I already installed GCC and know that gcc <filename> compiles the code.  However, when I try to type "a.out" to run the code (which is what I have done in class all semester) it says command not found. I am very new both to coding and to Linux, so this may be a very obvious mistake. All I am trying to do is compile (which I have managed) and run my code  I am also open to alternative methods for compiling and running code in Linux if anyone has any suggestions. Please be as detailed as possible in any explanations though, as I have said, I am new to Linux so layman terms would be best.

Thanks in advance

---

### Post by R Clemons on 2009-05-08
did you run ./a.out ?

---

### Post by ad_267 on 2009-05-08
Just to clarify, you need to run "./a.out" rather than just "a.out". Running a.out looks everywhere in your PATH environment variable for an executable called a.out. You can enter "echo $PATH" to see what directories are included there. You need to run ./a.out to tell your shell to look in the current directory for the executable.

You'll also probably want to install the build-essential package which contains headers and other things that are often needed when compiling software.

---

### Post by etheodos on 2009-05-08
Worked perfectly, thanks, you guys are my heroes.

---

