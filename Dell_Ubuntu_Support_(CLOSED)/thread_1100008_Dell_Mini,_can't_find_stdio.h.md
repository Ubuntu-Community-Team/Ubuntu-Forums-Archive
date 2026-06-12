---
title: "Dell Mini, can't find stdio.h"
date: 2009-03-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Aunger on 2009-03-18
I just bought a Dell Mini with Ubuntu 8.04 and I tried to check the C compiler in a terminal window with the following program named test.c:
/* test c program */
#include <stdio.h>
int main(){
printf("Hello world!\n");
}
I tried to compile it like this:
gcc test.c
and got the following error:
test.c:2:19: error: stdio.h: No such file or directory
The program compiles and runs fine on my desktop computer.
Any help would be appreciated.
Aunger

---

### Post by karlr42 on 2009-03-18
Have you got the compiler installed?
```
sudo apt-get install build-essential
```

---

### Post by Aunger on 2009-03-18
That fixed it!  Many thanks.  And that was the fastest help I have ever seen!
Aunger

---

