---
title: "compiling  C files"
date: 2009-04-16
forum: General Help
---

### Post by ayastona on 2009-04-16
hey im trying to compile this damn file..

this is what im typing:
```
gcc -Wall -g -o myprogram main.c `pkg-config --cflags --libs gtk+-2.0` -export-dynamic
```

when i hit enter this is what it says:
```
main.c:1: error: expected identifier or ‘(’ before ‘<’ token
main.c:2:27: error: too many decimal points in number
```

what gives?

---

### Post by Catdaddy on 2009-04-16
Definatly a problem with your code mang

Check around your preprocessor headers.

make sure it looks like 
#include <NAME.h>

---

### Post by lensman3 on 2009-04-16
What does line 1 and line 25 of main.c look like?  

The first error looks like you have garbage on the first line of the file.  

On line 27, there is a number that must have 2 or more decimals OR the number that is being used to initialize the variable has a decimal and the variable is defined as an int or long or the unsigned equivalents.

What do you get back if you add the following on a bash script line: `pkg-config --cflags --libs gtk+-2.0`.  The stuff between the back-ticks gets expanded into something.  Tell us what the expansion is?  This could be the problem too!

Hope this helps.

---

