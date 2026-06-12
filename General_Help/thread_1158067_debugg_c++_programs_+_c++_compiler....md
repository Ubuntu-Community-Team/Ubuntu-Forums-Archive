---
title: "debugg c++ programs + c++ compiler..."
date: 2009-05-13
forum: General Help
---

### Post by muctadir on 2009-05-13
how to debug c++ programs using ubuntu...???

is there any c++ compiler for ubuntu??? if yes, where can i get it??

please tell me..

thank you...........

---

### Post by hexanol on 2009-05-13
g++ is a C++ compiler for Linux.
gdb is a debugger.

Where you can get them ?
```
sudo aptitude install g++
sudo aptitude install gdb
```

---

### Post by muctadir on 2009-05-13
how to use it or open it???

pls, tell me........

---

### Post by hexanol on 2009-05-13
You can find the manual for gcc (g++ is part of gcc) [here]("http://gcc.gnu.org/onlinedocs/"). You can find which version of gcc you have with the command "gcc --version".

Example on how to use g++
```
$ cat > main.cpp << EOF
#include <iostream>

int main()
{
   std::cout << "Hello, world!\n";
   return 0;
}

EOF
$ g++ main.cpp
$ ./a.out
Hello, world!
$

```

You can find the manual for gdb [here]("http://sourceware.org/gdb/current/onlinedocs/gdb_toc.html").

gdb is a bit hard to use the first time.

Oh, and you can also look at the man pages for g++ and gdb. You can also do more search on the web and try to find tutorials.

---

### Post by muctadir on 2009-05-13
thank you.......

---

### Post by gamblor01 on 2009-05-13
gcc and gdb both get installed as part of the build-essential package.  If you plan on building anything from source on your machine, you're probably going to eventually want it so I would suggest you do:

```

sudo apt-get install build-essential

```


This isn't necessary if you are just going to be compiling some simple C/C++ programs that you write, but if you happen to download the source for a large program, sometimes you need certain libraries and kernel info that is installed as part of the build-essential package.  If you have the hard drive space it's useful.

---

