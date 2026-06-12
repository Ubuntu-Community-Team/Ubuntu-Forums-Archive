---
title: "how is cashed memory different?"
date: 2009-04-14
forum: General Help
---

### Post by Kain000 on 2009-04-14
hey this is a totally noob question, but i'm looking at my system monitor applet and it's showing 11% memory in use, and 83% is cashed.  but it will also show me when there is 'free' memory, so my question is what does it mean for memory to be cashed, it's not being used by me i dont think, so is it like a background process?

---

### Post by soltanis on 2009-04-14
[http://en.wikipedia.org/wiki/Cache](http://en.wikipedia.org/wiki/Cache)

Caching is storing information in memory where it can be quickly retrieved later, when it is needed. This is generally done when applications need to modify a set of data efficiently.

---

### Post by maheshasolkar on 2009-04-14
When you open a program, it is loaded into the system memory (RAM) from the disk. At this point it occupies some memory. This is the part of 'memory in use'.

When you close the program, the memory is not needed anymore. But the OS does not physically remove the bits from memory, merely marks it 'up for grabs'. This is the cached part of the memory.

If you open the program that you just closed once again, while it is still sitting in the memory, it need not be loaded from the disk. The OS knows it already resides in the memory. Hence it is faster to load.

If you open some other program that requires more space in the memory, than there is free, it may take the cached portion of the memory.

Most of the above also applies to data files, not just programs.

The above is my understanding. Please correct me if I am wrong.

---

### Post by Kain000 on 2009-04-14
thanks both of you, this explains alot.

---

