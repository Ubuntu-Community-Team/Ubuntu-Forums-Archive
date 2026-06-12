---
title: "stdio.h: No such file or directory"
date: 2009-01-24
forum: General Help
---

### Post by AlexAlk on 2009-01-24
Hey!

In my school I learn programming with C!
And when i will run a programm, this error "stdio.h: No such file or directory" came!

Code:

#include <stdio.h>
int main()
{
  printf("Hello world\n");
  return 0;
}

How can i install the stdio.h?

I attempt that i use this:
                          sudo apt-get install build-essential
then came this: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

then i use this: dpkg --configure -a
and then i need Super User Rechte!

How I became Super User????

Many greetings!

---

### Post by jespdj on 2009-01-24
> **AlexAlk said:**
> How I became Super User????
By using sudo:
```
sudo dpkg --configure -a
```
For more info see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You indeed need to install the package **build-essential** to get stdio.h and other standard header files. You can do it with sudo apt-get ..., or with Synaptic (System > Administration > Synaptic Package Manager).

After installing this, compile your program like this (assuming you saved it in a file named hello.c):
```
gcc hello.c -o hello
```
And then run it like this:
```
./hello
```

---

