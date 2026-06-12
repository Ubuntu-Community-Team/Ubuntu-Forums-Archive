---
title: "1 GB of Ram..."
date: 2006-06-17
forum: Desktop Environments
---

### Post by 3zrael on 2006-06-17
Hello,
I installed 1 gb of ram in kubuntu, two kingston 512mb  modules. There's something strange about that: during the bootstrap I can clearly see that the bios says "1048576 K", while Top, once linux has loaded, says "1036096 K"...
WHY???

thx in advance!

---

### Post by x64Jimbo on 2006-06-17
Do you maybe have shared video memory? I have 1GB installed in my computer but it only shows up as 900 something megs because the motherboard uses system memory to power the video card.

---

### Post by 3zrael on 2006-06-17
I have a radeon 9600pro with its own memory... but I really don't know...

---

### Post by x64Jimbo on 2006-06-17
Well, another possibility is you could be looking at that classic confusion between MB and MiB. For more info, go here:
[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)

---

### Post by 3zrael on 2006-06-17
well, you could be right, but in wiki I have:
1GB=1,073,741,824
and in my kinfocenter I read:
Tot Physical Memory: 1,060,962,304

Obviously I do not care about the missing few megs, but
I suspect there's something wrong with my modules.

Thank you for your help, anyway.

---

### Post by 3zrael on 2006-06-17
Ok.
Everything seems all right with my ram, it must be something related with how the kernel handles it.

Sure it is strange!
Bios says: 1048576k
Linux says: 1036096k
Win says: 1048048k

:confused:

---

### Post by Ramses de Norre on 2006-06-17
I think top doesn't show the amount of memory taken by the kernel, because this memory can't be used by any other program (while other things in memory can be moved to swap).

---

### Post by 3zrael on 2006-06-17
The strange thing is that even kinfocenter says something that could seem wrong:

"Total physical memory: 1,060,962,304 Byte = 1,011.81 Mbyte"

...while 1GB should be (1024*1024*1024) equal to 1,073,741,824.

:?:

---

