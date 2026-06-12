---
title: "problem using gcc"
date: 2009-05-07
forum: General Help
---

### Post by anirup on 2009-05-07
i am having problems using gcc and g++ in ubuntu.it is installed allright
because i completely removed the packages and then reinstalled.
[B]if i run i get these errors.i have kubuntu too and i have no problems in it.i have both gcc-3.4 and gcc-4.2 installed.but no probs in kubuntu.
 [/B]
[B]anirupdutta@HCL:~$ cc a.c 
cc: error trying to exec 'cc1': execvp: No such file or directory
anirupdutta@HCL:~$ g++ a.c 
g++: error trying to exec 'cc1plus': execvp: No such file or directory
anirupdutta@HCL:~$ gcc a.c
gcc: error trying to exec 'cc1': execvp: No such file or directory
anirupdutta@HCL:~$ c++ a.c
c++: error trying to exec 'cc1plus': execvp: No such file or directory
anirupdutta@HCL:~$ 
[/B]

---

### Post by _Purple_ on 2009-05-07
Try
```
gcc a.c -o a
```
```
./a
```

---

### Post by geirha on 2009-05-07
Do the cc1 and cc1plus executables exist?
```
find /usr/lib/gcc -name cc1 -o -name cc1plus
```

---

### Post by lloyd_b on 2009-05-07
Start by installing the "build-essential" package - "sudo apt-get install build-essential" in a terminal window, or use the package manager of your choice.

Lloyd B.

---

