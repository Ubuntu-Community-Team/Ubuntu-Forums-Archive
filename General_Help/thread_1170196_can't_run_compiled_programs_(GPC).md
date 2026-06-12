---
title: "can't run compiled programs (GPC)"
date: 2009-05-26
forum: General Help
---

### Post by Trae on 2009-05-26
Hello,

I'm running the x86 build of Ubuntu because and I've been wanting to start working with compiling some pascal programs.  I like GPC so I went ahead and installed it using the command


> sudo apt-get install gpc

next I went about writing a simple "hello world" application and compiled it with the command

> gpc hello.pas

which produced what should be a compiled file in a.out.  The problem is I'm not really sure what I do with that file.  I tried 

> bash a.out

but what I got back was 

> a.out: a.out: cannot execute binary file

I've also tried using FPC and I have the same problem.  What's going on? :(

*edit* lol i typo'd the title ><

---

### Post by mr_mop on 2009-05-26
> **Trae said:**
> 
bash a.out


You are trying to pass a binary file to bash where it is expecing
an ascii file that contains bash commands.
To run your compiled code try ./a.out instead.

---

