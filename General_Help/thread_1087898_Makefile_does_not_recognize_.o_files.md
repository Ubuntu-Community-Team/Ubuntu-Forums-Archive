---
title: "Makefile does not recognize .o files"
date: 2009-03-05
forum: General Help
---

### Post by jmh2cv on 2009-03-05
Hey All,

I just installed 8.10, and am in the process of checking for bugs. I just ran into the following, which runs just fine on Cygwin in Windows Vista:

```

justin@justin-laptop:~/Documents/School/Current Classes/CS216/Lab5$ make
g++  -Wall -g pizza.o pizzadough.o tomatosauce.o toppings.o mushrooms.o peppers.o cheese.o pepperoni.o -o pizza
pizza.o: file not recognized: File format not recognized
collect2: ld returned 1 exit status
make: *** [pizza] Error 1

```

I have the make package installed. Any thoughts on why its not recognizing object files?

---

### Post by heindsight on 2009-03-05
Not sure, but if the .o files were created on windows, then they're most probably in a different format than that used in GNU/Linux. If you have the source files, try deleting all the .o files and then run make again.

By the way, it's not make that's complaining about the .o files, make runs g++ which calls on ld to link the object files into an executable and it's actually ld that's doing the complaining.

EDIT:
Just another comment, make sure you have build-essential installed:
```
sudo apt-get install build-essential
```

---

### Post by jmh2cv on 2009-03-05
Your absolutely right. Thanks for the help.

---

