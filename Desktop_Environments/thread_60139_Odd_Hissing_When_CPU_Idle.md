---
title: "Odd Hissing When CPU Idle"
date: 2005-08-26
forum: Desktop Environments
---

### Post by jpoe on 2005-08-26
Hi all,

Again I have a really weird problem, and I was wondering if anyone has experienced anything like this before.  Whenever my CPUs (I'm using a dual core X2) are idle, there is a hissing sound that comes from my sound card.  Its very low when I use my crappy PC speakers; but very annoying on my headphones.  I noticed this only occurs when 1 or both of the CPU's is idle (in fact, the problem compounds ... the hissing is twice as loud when both idle).

I have come up with a temporary solution that is about as unelegent as is imaginable.  I wrote a c program, cpurburn.c :

```
#include<stdio.h>

int main()
{
     fork();
     while(1);
}
```

Which I run using the nice command:

```
nice -n 19 ./cpuburn
```

As I said, I don't think you could come up with a less elegant fix; however I'm not sure what else to do.  Anyone have any suggestions, or know what might be causing something like this?

Thanks as always!

---

### Post by KingBahamut on 2005-08-26
Thats the Gremlin sitting on your CPU cooking away. 

Sorry, I just couldnt help that one. 

Thats puzzling , though I aggree that isnt the most elegant way to address the issue.

---

