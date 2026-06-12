---
title: "how to compile my own .cpp source code files"
date: 2009-02-13
forum: General Help
---

### Post by coolethan on 2009-02-13
i'm learning c++ but i don't know how to compile the code. generally when compiling anything else i can just type ./configure, make, sudo make install, blah blah blah but how do i do it for my own code using the terminal or if theres is a sweet compiler out there i should try let me know.

---

### Post by bhaverkamp on 2009-02-13
If you have been configure/make'ing then you already have the compiler install'd. 
If not 'sudo apt-get install build-essentials' will get you setup.
If you have a simple single file program than 'gcc hello.cpp' should get you started.

---

### Post by PmDematagoda on 2009-02-13
You would need to use g++.

This should be how you compile a single source file written in C++:-
```
g++ name-of-source.cpp -o output-file
```

---

### Post by coolethan on 2009-02-13
ok sweet thanks, ya i was aware of the compilers i just didn't really know how to apply them to my own stuff.

---

