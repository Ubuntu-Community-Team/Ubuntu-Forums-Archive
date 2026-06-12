---
title: "error in c++ code in ubuntu"
date: 2011-09-29
forum: Education &amp; Science
---

### Post by emab on 2011-09-29
I am trying to use [Goblin library]("http://goblin2.sourceforge.net/") which is used for special network algorithms. This library provides some header files and objects in C/C++ So, you can easily add a header file and use some special classes and functions.

Unfortunately, when I add the header file, I get error. In the following you can see the simple code and error.

Code:
```
#include<goblin.h>

int main()
{
    return 0;
}
```

Error:
```
$ g++ -o test.o test.cpp
/tmp/ccB0Rb25.o: In function `goblinRootObject::~goblinRootObject()':
test.cpp:(.text._ZN16goblinRootObjectD1Ev[goblinRootObject::~goblinRootObject()]+0x10): undefined reference to `goblinNObjects'
test.cpp:(.text._ZN16goblinRootObjectD1Ev[goblinRootObject::~goblinRootObject()]+0x18): undefined reference to `goblinNObjects'
test.cpp:(.text._ZN16goblinRootObjectD1Ev[goblinRootObject::~goblinRootObject()]+0x2c): undefined reference to `goblinRootObject::operator delete(void*)'
/tmp/ccB0Rb25.o: In function `goblinRootObject::~goblinRootObject()':
test.cpp:(.text._ZN16goblinRootObjectD0Ev[goblinRootObject::~goblinRootObject()]+0x10): undefined reference to `goblinNObjects'
test.cpp:(.text._ZN16goblinRootObjectD0Ev[goblinRootObject::~goblinRootObject()]+0x18): undefined reference to `goblinNObjects'
test.cpp:(.text._ZN16goblinRootObjectD0Ev[goblinRootObject::~goblinRootObject()]+0x2c): undefined reference to `goblinRootObject::operator delete(void*)'
collect2: ld returned 1 exit status
```

Can anybody help me please?

---

### Post by Porcini M. on 2011-09-29
Looks like you need to include a library for g++ to link. It would be an extra flag, something like "-lgoblin" (look up what that library should be for goblin).

---

### Post by emab on 2011-09-29
> **Porcini M. said:**
> Looks like you need to include a library for g++ to link. It would be an extra flag, something like "-lgoblin" (look up what that library should be for goblin).
yes, thank you very much.
It worked!!

---

