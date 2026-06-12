---
title: "games wont stay in fullscreen"
date: 2008-03-02
forum: Gaming &amp; Leisure
---

### Post by 1467 on 2008-03-02
after 5 minutes of playing a game it go back to my desktop and will not stop is thar a way to fix this?

---

### Post by agtownz on 2008-03-02
Any specific games or all games?  Is it always after exactly 5 minutes of playing?

---

### Post by 1467 on 2008-03-03
around 5 minutes or so and it will go back to fullscreen and repeat  on netpazer alien arena and tremulous

---

### Post by jasonbrisbane on 2008-03-07
Hi,m

Turn off Compiz. It caused all sorts of problems, including this in tremulous with my system.

BTW: its also known as special effects or desktop effects.(IIRC)

Regards,
Jason Brisbane

---

### Post by Toffeeapple on 2008-03-07
Try turning off screensaver and powersaving for the monitor..

---

### Post by Perfect Storm on 2008-03-07
> **jasonbrisbane said:**
> Hi,m

Turn off Compiz. It caused all sorts of problems, including this in tremulous with my system.

BTW: its also known as special effects or desktop effects.(IIRC)

Regards,
Jason Brisbane

Bingo!

I'll always make a script to turn it on/off.

eg. 
For riotball
```
 #!/bin/bash
metacity --replace &
cd ~/.Games/riotball
./run_riotball -f
compiz --replace &
```

---

### Post by TaTaE on 2008-05-04
There are two solutions for this. Try one of these:

1. Start Advanced Compiz Settings and disable "Unredirect Fullscreen Windows" in "General Options --> General".
2. Second solution is here [http://ph.ubuntuforums.com/showpost....2&postcount=10](http://ph.ubuntuforums.com/showpost....2&postcount=10)


Cheers,

---

