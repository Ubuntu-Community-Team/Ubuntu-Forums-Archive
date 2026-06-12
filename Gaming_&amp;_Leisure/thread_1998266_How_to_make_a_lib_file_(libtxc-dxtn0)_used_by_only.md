---
title: "How to make a lib file (libtxc-dxtn0) used by only the apps that need it?"
date: 2012-06-06
forum: Gaming &amp; Leisure
---

### Post by deckoff on 2012-06-06
I need **libtxc-dxtn** for Amnesia  to run . Without it, the game crashes. If I install it, the colors some other games drastically change - namely Civ 5 under wine. So, I install and un-install the package, depending on what I want to start.

Is there a way to provide the lib to the apps that only need it? I got some advices to try LD_LIBRARY_PATH or .and LD_PRELOAD , but info I got is too advanced to follow, so I would ask for clearer instructions.
I have uninstalled the lib, unzipped the deb packaged and extracted the lib itself. 
Who should be the owner of the lib (root, me , anyone else)?
Where should I put it ( anywhere)
Should the lib have permission to run or not? I tried both - with no permissions I got no permissions, with i got core dumped...

---

### Post by oldrocker99 on 2012-06-06
You could try placing the .so file in the game directory itself; since it's not in your PATH$, no other prograns should use it (I think).

---

### Post by deckoff on 2012-06-08
```


LD_PRELOAD='/home/deckoff/Desktop/libtxc/libtxc_dxtn.so' /opt/amnesia/Launcher.bin

```

This did it. I set lib owner to root and marked the lib as executable. I dont know if thi is needed or not. I have made a syntax error in my first tries- I have left some space between "=" and "'"

---

