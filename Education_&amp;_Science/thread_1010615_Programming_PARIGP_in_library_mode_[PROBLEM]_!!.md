---
title: "Programming PARI/GP in library mode [PROBLEM] !?!"
date: 2008-12-13
forum: Education &amp; Science
---

### Post by Mxmler on 2008-12-13
Hi all,

I am tired with PARI/GP packages. I don't know whats the problem.
The following should be executed normally.

I installed the following packages
libpari2-gmp
libpari-dev

as well as pari-gp

#include <pari.h>
int main()
{
  pari_init(100000,0);
  return 0;
}

and all what I got is an error messages (the main one: No such file or directory for pari.h)

Can you help me please and show me step by step how to make this done? Do I need to add linkage between my app. and the library?

Thanks in advance.

---

### Post by billgarcia on 2008-12-21
It looks like installing those packages places all those header files in /usr/local/include/pari. Go ahead and check to see if that's true for you. I just copied all those headers to /usr/local/include, and I was able to compile a test document using g++ successfully. I also added the -lpari flag to g++. Here's my source for the test code:

```


#include<pari.h>

using namespace std;

int main(){

 pari_init(10000000, 1000000);

 return 0;

}


```

The above compiles successfully with the command:

```
g++ test.cpp -lpari
```

Of course, test.cpp is the name of the source file. By the way I've been driving myself crazy with this all night, so don't feel like you're the only one! :-)

---

