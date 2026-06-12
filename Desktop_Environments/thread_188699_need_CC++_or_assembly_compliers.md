---
title: "need C/C++ or assembly compliers"
date: 2006-06-04
forum: Desktop Environments
---

### Post by shorty666 on 2006-06-04
I was wondering if there were any good, ubuntu compatible C,C++, or assembly compliers. All I compliers that I saw available were for python or other languages I didn't know. I have an outdated version of turbo C and I don't think it is compatible. :confused: :-k

---

### Post by taurus on 2006-06-04
There is GNU C, gcc.  Open a terminal, Applications -> Accessories -> Terminal, and type
```

sudo apt-get install build-essential

```
Now, you can check to see which version of gcc you have by running from a terminal,
```

gcc -v

```

---

### Post by Stone123 on 2006-06-04
[QUOTE=shorty666]I was wondering if there were any good, ubuntu compatible C,C++, or assembly compliers. All I compliers that I saw available were for python or other languages I didn't know. I have an outdated version of turbo C and I don't think it is compatible. :confused: :-k[/QUOTE]

gcc/g++ for c/c++ or you some development environment .
Assambley depends on processor you plan to code for mips , intel . motorola.
Check out ubuntu wiki on how to use synaptic.

---

