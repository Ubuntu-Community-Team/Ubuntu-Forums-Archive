---
title: "pthread linking issue with Eclipse"
date: 2009-12-12
forum: Desktop Environments
---

### Post by reggler on 2009-12-12
Hi all,

I installed eclipse 3.5.1 from the repo and added CDT to it. Now i would like to compile a multithreaded application that's making use of the pthread library. On the console i just pass the -pthread flag to my compile command and that works fine but if i added pthread to the linker libraries in eclipse i get following:
```

**** Build of configuration Release for project test1 ****

make all 
Building target: test1
Invoking: GCC C Linker
gcc  -o"test1"  ./src/test1.o   -lpthread
Finished building target: test1
```

Why would it not be able to find my pthread library???

Thanks alot for your help!

---

