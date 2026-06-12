---
title: "[SOLVED] Lost border and terminal window completely white"
date: 2008-09-30
forum: Desktop Environments
---

### Post by teuffel2 on 2008-09-30
I did a change to fix the resolution. Now I have lost my window border and when I bring up the terminal I get a white box. I have scoured the threads but alas I have not found a cure for either of these problems. Can someone help? I deleted emerald and re-installed it with no luck. Many thanks in advance.

---

### Post by anotherdisciple on 2008-09-30
I noticed that you don't have any replies so far, so I'll just give you something to try.

Hit Alt+F2 and type 
```
metacity --replace
```

Tell me what happens.

If that doesn't work... try:
```
gtk-window-decorator --replace
```

---

### Post by teuffel2 on 2008-09-30
Wow! Many thanks. Metacity did it. Can't thank you enough.

---

