---
title: "adom?"
date: 2007-08-09
forum: Gaming &amp; Leisure
---

### Post by Tyke91 on 2007-08-09
i've downloaded (and i think i've installed) adom

i followed all the instructions in the readme for someone with access to root, but when i try to run adom - i get this message

```
mykola@MykolaUbuntu:~$ adom

Ancient Domains Of Mystery -- Version 1.1.1 
(C) Copyright 1994-2002 Thomas Biskup. 
All Rights Reserved. 

/* 
 * ADOM session aborted due to an external problem. 
 * Problem Description: ADOM requires at least a 25x77 screen to run on. 
 */ 



```

what am i doing wrong?

---

### Post by rayj on 2008-04-06
I'm now having this exact same issue. Is there a command line option I need to include? Maybe a config line to add?

---

### Post by Belliinator on 2008-04-06
> **Tyke91 said:**
> i've downloaded (and i think i've installed) adom

i followed all the instructions in the readme for someone with access to root, but when i try to run adom - i get this message

```
mykola@MykolaUbuntu:~$ adom

Ancient Domains Of Mystery -- Version 1.1.1 
(C) Copyright 1994-2002 Thomas Biskup. 
All Rights Reserved. 

/* 
 * ADOM session aborted due to an external problem. 
 * Problem Description: ADOM requires at least a 25x77 screen to run on. 
 */ 



```what am i doing wrong?

Try resizing the terminal to 25 * 77 by clicking and dragging the the bottom right corner of the screen. It will tell you as you drag it what size it is. By the looks of things the game is installed and there is another issue. (which I think is the terminal size)

Edit: Hang on, 25 * 77 is huge isnt it? Maybe try 77*25, but im not sure.

---

### Post by beerslayer on 2008-10-21
I realize this is an old thread, but...

I just had the same problem, and found the resolution.

The default term window in Ubuntu (8.04) is 80x24.  I guess ADOM desperately needs just one more line.  I dragged the bottom edge of the window until it stretched to (at least) 80x25.  Now ADOM works.

I'm a n00b and don't know how to force new terminal windows to default to 80x25, so I guess I'll have to do this each time.  But at least it works.

---

