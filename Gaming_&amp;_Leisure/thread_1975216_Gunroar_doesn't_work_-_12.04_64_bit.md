---
title: "Gunroar doesn't work - 12.04 64 bit"
date: 2012-05-07
forum: Gaming &amp; Leisure
---

### Post by BigSilly on 2012-05-07
Installed all the juicy Kenta Cho shooters from the Precise repositories last night, but only Gunroar doesn't work. 

```
bigsilly@bigsilly:~$ gunroar
Error: circular initialization dependency with module abagames.gr.particle
```

Any ideas? Google reveals naught. Thanks all.

---

### Post by xperienc3d on 2012-07-10
I had exactly the same issue on 2 PCs - AMD Athlon II X4 630/4 Gb  DDR3 1333/AMD Radeon HD 6670 1Gb/ running Ubuntu 12.04 64-bit and on EEE PC 701 running lubuntu 12.04 32 bit, so the issue most probably pertain to the game version in repos. After downgrading to version 1.3 (current is 1.5), the game runs well on both rigs.

---

### Post by BigSilly on 2012-08-13
Bit late, but thanks for the solution. I managed to download Debian's version of Gunroar 0.15 1-3, as opposed to the 1-5 version in Ubuntu's repositories, and yes you are right it works perfectly. Many thanks again. :)

---

