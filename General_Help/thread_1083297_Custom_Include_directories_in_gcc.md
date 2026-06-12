---
title: "Custom Include directories in gcc"
date: 2009-02-28
forum: General Help
---

### Post by Gannon8 on 2009-02-28
Hello

This is my first time using gcc (just by itself, not with make). I am wondering how to add directories to search for includes.

Say I have this program:
```
#include "game.h"
chat_interface *chat;
void print_hello(Arena *arena)
{
    chat->SendMessage(arena, "Hello");
}
```
and game.h is in ./include/game.h
I was wondering how I could do this, as in what arguments to pass.

Thank you for your time

---

### Post by snova on 2009-02-28
Use the -I flag:

```
gcc source.c -o program -Iinclude
```

---

### Post by Gannon8 on 2009-02-28
Thank you snova. Unfortunately, it appears that it is not including items from the root directory (eg, include/game.h needs packets/weapon.h).

---

### Post by ad_267 on 2009-02-28
Can't you just do:
```
gcc source.c -o program -Iinclude -Ipackets
```

---

### Post by Gannon8 on 2009-02-28
I did:
```
gcc source.c -o program.so -I./include -I./ -Wall
```
Gave me a bunch of errors about structs/functions in a source file that I included not being there.

It compiles into a .dll fine with Dev-C++ in windows.

EDIT: It also says atan2 from math.h doesn't exist

---

### Post by Gannon8 on 2009-02-28
Ok, I heard that that program shouldn't be compiled on x86_64. Seeing as Ubuntu on my laptop just blew up... Emulator time.

---

### Post by Gannon8 on 2009-03-01
Fixed ubuntu on my laptop, but gives the same errors as before.

---

### Post by Gannon8 on 2009-03-01
Well, apparently I was supposed to compile something else along with it. Problem solved

---

