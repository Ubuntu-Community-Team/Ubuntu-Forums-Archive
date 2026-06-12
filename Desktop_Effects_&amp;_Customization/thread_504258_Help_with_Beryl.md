---
title: "Help with Beryl"
date: 2007-07-18
forum: Desktop Effects &amp; Customization
---

### Post by ErusGuleilmus on 2007-07-18
Whenever I try to run the desktop effects in 7.04 or run Beryl, all of the window borders vanish. I'm sure that there is a real easy fix i just don't know where to look . Thank you for your effort!

---

### Post by ThrobbingBrain66 on 2007-07-18
When you run Beryl, for example, you also have to run either emerald with it.  So, to run it as one line:
```
 beryl --replace -c emerald --replace
```

Run that in a terminal and post back with any success or failures.

---

### Post by ErusGuleilmus on 2007-07-18
No dice. Here is what happens:

william@william-laptop:~$  beryl --replace -c emerald --replace
beryl: invalid option -- c
william@william-laptop:~$  beryl --replace -c emerald --replace

---

### Post by ThrobbingBrain66 on 2007-07-19
I'm sorry, try it without the -c then, that wasn't supposed to be there.

---

### Post by ErusGuleilmus on 2007-07-19
No, that still didnt work. it ran in the terminal and it said that everything was ok and detected that I use Nvidia, but still no window borders.

---

### Post by family on 2007-07-19
Same troubles...:(

---

### Post by ErusGuleilmus on 2007-07-20
So, is this a way of saying that no one has any clue?

---

### Post by ukulele_ninja on 2007-07-20
I had the same problem when I tried to run beryl and it was because my graphics card couldn't handle 3-d graphics or something. THe one I have that seems to be common for these problems is the ATI Radeon XPress 200M. Im still trying to figure out how to get doing 3d graphics.

---

### Post by ErusGuleilmus on 2007-07-20
Th Graphics card is a Nvidia Go 2100. It should be able to handle 3d, it does with everything else. The desktop effects work but the only problem is that the window borders are gone.

---

