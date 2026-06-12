---
title: "gdb throwing &quot;No symbol table is loaded&quot;"
date: 2009-01-02
forum: General Help
---

### Post by Cyclops_ on 2009-01-02
Hey, all,

I am trying to get "clewn" to work so that I can do PHP debugging with gVim through gdb.

I have clewn installed and gdb and vim (even upgraded to vim 7.2) ...

I will run clewn, which brings up an instance of gvim and starts gdb.  Then when I try to set a breakpoint, I run into the following error (in gdb):

```

No symbol table is loaded.  Use the "file" command.

```I tried compiling gdb from source, and attempted to "compile with the -g option" (or tried to figure out how to do that anyway).... since I am a complete n00b at compiling things beyond the basic ./configure, make, make install.....

Any help would be GREAT!

Thanks!!!

---

### Post by Cyclops_ on 2009-01-03
*bump*

(anyone?)

---

### Post by scribbles on 2011-07-24
The -g flag is important for the compiler to include debugging info in the binary.

```
g++ -g yourcode.cc -o yourcode
```

In case it comes up in searches!

---

