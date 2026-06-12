---
title: "Gcc"
date: 2009-05-21
forum: General Help
---

### Post by JafaarNhh on 2009-05-21
I have installed gcc but i don't know how to compile my source code please help im a Newbie.
Im running Ubuntu 9.04

---

### Post by baseface on 2009-05-21
read the man page.
```
gcc -o program program.c
```

---

### Post by JafaarNhh on 2009-05-21
It didnt work it says
```
gcc -o program program.c
gcc: program.c: No such file or directory
gcc: no input files

```

---

### Post by baseface on 2009-05-21
are you substituting "program" and "program.c" for the names of what you want your program to be called and the name of the source file?

---

### Post by _Purple_ on 2009-05-21
```
gcc program.c -o program
```

Then run using
```
./program
```

---

### Post by JafaarNhh on 2009-05-21
baseface i didnt quit understand you can you please tell me how to find the file i wrote because i wrote the code in an editor and saved it in the desktop

---

### Post by baseface on 2009-05-21
```
cd /directory/where/code/is
```
then run gcc.

---

### Post by JafaarNhh on 2009-05-21
Thanks this problem is SOLVED!:D:D:D:D:D

---

