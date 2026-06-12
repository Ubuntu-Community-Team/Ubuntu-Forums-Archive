---
title: "error: ‘exit’ was not declared in this scope"
date: 2009-01-07
forum: General Help
---

### Post by jkuiliu on 2009-01-07
someone plzz help me

i get the following errors after i compile my program!!

[I]jack@jack-desktop:~/Desktop/test/Q1$ make
g++ -o run main.cpp
main.cpp: In function ‘int main()’:
main.cpp:26: error: ‘exit’ was not declared in this scope
make: *** [run] Error 1[/I]

after i comment out then line exit(0) in the main.cpp;

my program is compiled perfectly

??????????????????????????
what's going on here? 
what should i do to fix this error?:confused:
??????????????????????????

---

### Post by jkuiliu on 2009-01-07
here is the code;D

---

### Post by vs55 on 2010-02-28
it will be compiled without errors if you include in your code the statement:

#include <cstdlib>

---

