---
title: "g++ error"
date: 2008-10-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fhhs on 2008-10-13
hello


i so need help on this
as i type: g++ filename.cpp -o filename it gives me this weird message on my ubuntu:

/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
collect2: ld returned 1 exit status



i have no idea what this is i am using class functions here...plzz help me out
i appreciate any help.

---

### Post by jamesrl on 2008-10-13
Try compiling with the -c option ([solution from here]("http://ubuntuforums.org/showpost.php?p=4603600&postcount=3")) if that doesn't work, read on.

Do you get this error for compiling extremely simple programs?

such as:
```

#include <iostream>
using namespace std;

int
main() {
    cout  << "Hello World" << endl;
    return 1;
}

```

I believe crt1.o is part of glibc so maybe you have incompatible versions of glibc and g++ and/or gcc-lib-dev

---

### Post by roelpeeters on 2008-10-13
Hi! I think first of all your post belongs in Programming Talk instead of the Dell Forums. Maybe a moderator can move this post?
Onto your question: it seems like you are missing a 'main' function. It is necessary for g++ to create a runnable program. (Main is the first function in your program that will be called.) You might want to copy the source of jamesrl to try that out.

Could you post your program?

The option -c only compiles the code and creates a so-called object file. This file needs to be linked with other object files (one of which contains the main function) to form a running program.

Hope this helps,

Roel

---

