---
title: "Odd gcc errors"
date: 2005-09-28
forum: Desktop Environments
---

### Post by cwu on 2005-09-28
Hi,

I just installed Ubuntu yesterday. I've been trying to test out my installtion of gcc. When I compile it, I got:
main.cpp:1:20: error: stdlib.h: No such file or directory
main.cpp:2:19: error: stdio.h: No such file or directory
main.cpp:3:20: error: assert.h: No such file or directory
main.cpp:6:21: error: gl/glut.h: No such file or directory
... among other things.

I've clearly set something up incorrectly. Any ideas why the compiler can't find something as innocuous as stdlib?

Chris

---

### Post by cwu on 2005-09-28
Perhaps I should also add that it does the same thing with C++ libraries like iostream...

---

### Post by YourSurrogateGod on 2005-09-28
1) gcc doesn't compile .cpp files, g++ does. Use the below command...
```
g++ -o stuff stuff.cpp
```
2) There are no stdlib.h, iostream.h or stdio.h files in C++ anymore, those are not part of the standard, so they were gotten rid of in the newer compiler. For stlib.h try #include <cstlib> and for iostream.h #include <iostream>

I've never used glut, but I'm guessing that you have to use a special command when compiling a file with it. Speaking of which, how did you compile your source?

---

### Post by cwu on 2005-09-28
Yes, so I guess I should be more explicit. Forget the opengl/glut stuff. It's kind of more basic than that. 

So if stuff.c is:
****************
#include <stdio.h>
int main(void)
{
  printf("Hello World!\n");
  return 0;
}
*****************
and I run
% gcc -o stuff stuff.c

then I get:
stuff.c:1:19: error: stdio.h: No such file or directory
stuff.c: In function ‘main’:
stuff.c:4: warning: incompatible implicit declaration of built-in function ‘printf’

With respect to g++, if stuff2.cpp is
********************************
#include <iostream>
using namespace std;
main()
{
    cout << "Hello World!";
    return 0;
}
*******************************
then I get:
In file included from /usr/include/c++/4.0.2/i486-linux-gnu/bits/c++config.h:35,                 from /usr/include/c++/4.0.2/iostream:43,
                 from stuff2.cpp:1:
/usr/include/c++/4.0.2/i486-linux-gnu/bits/os_defines.h:39:22: error: features.h: No such file or directory
In file included from /usr/include/c++/4.0.2/i486-linux-gnu/bits/c++locale.h:41,                 from /usr/include/c++/4.0.2/iosfwd:45,
                 from /usr/include/c++/4.0.2/ios:43,
                 from /usr/include/c++/4.0.2/ostream:44,
                 from /usr/include/c++/4.0.2/iostream:44,
                 from stuff2.cpp:1:
/usr/include/c++/4.0.2/cstring:51:20: error: string.h: No such file or directoryIn file included from /usr/include/c++/4.0.2/i486-linux-gnu/bits/c++locale.h:42,                 from /usr/include/c++/4.0.2/iosfwd:45,
                 from /usr/include/c++/4.0.2/ios:43,
                 from /usr/include/c++/4.0.2/ostream:44,
                 from /usr/include/c++/4.0.2/iostream:44,
                 from stuff2.cpp:1:
/usr/include/c++/4.0.2/cstdio:52:19: error: stdio.h: No such file or directory
In file included from /usr/include/c++/4.0.2/i486-linux-gnu/bits/c++locale.h:43,                 from /usr/include/c++/4.0.2/iosfwd:45

... 
and similar stuff for a hundred lines or so....

So yeah, it's really two seperate things. I should have been more clear.

Thanks for the help.

---

### Post by YourSurrogateGod on 2005-09-28
How did you install gcc? Through synap (the gui that is)? I think I'll take a guess that libc6-dev is missing (not 100% sure.)
Why don't you try uninstalling and installing gcc again.

---

### Post by Zwack on 2005-09-28
Sounds like you don't have libc6-dev installed.

Mark the build-dev package and you should get everything you need to be able to compile.

Z.

---

### Post by cwu on 2005-09-29
Fantastic, that fixed. Thanks very much for the help.

---

