---
title: "problems with RAM"
date: 2009-06-21
forum: General Help
---

### Post by zeek333 on 2009-06-21
Hi, 

I'm new with linux,

btw i install ubuntu srv 9.04 and in system info it shows me only 234MB of memory but i have 3GB (2c512 2x1024 ) i tryed diferent way but no changes. Bios recognise. win as well. How is possible to fix it plz? 

My system: Dell optiplex745

---

### Post by sdennie on 2009-06-21
What is the output of:

```

free -m

```

---

### Post by zeek333 on 2009-06-21
free -m shows 

total 229 used 225 free 3 shared 0 buffers 4 cached 63
-/+ buff cache used 157 free 71 

swap total 666 used 124 free 542

---

### Post by Cheesemill on 2009-06-21
Have you tried running memtest from the boot menu?

---

### Post by zeek333 on 2009-06-21
cheers [Cheesemill]("http://ubuntuforums.org/member.php?u=559258") i found a problem was some changes in bios now it's ok 

should i change size of swap now cos when i install in begin like a 234 mb ram, swap was   made 666 mb 

i red somewhere that swap sould be 2 times biger than ram???

---

### Post by JordyD on 2009-06-21
> **zeek333 said:**
> cheers [Cheesemill]("http://ubuntuforums.org/member.php?u=559258") i found a problem was some changes in bios now it's ok 

should i change size of swap now cos when i install in begin like a 234 mb ram, swap was   made 666 mb 

i red somewhere that swap sould be 2 times biger than ram???

Your swap should be fine. That's an old rule of thumb that doesn't really mean much now-a-days because swap isn't used much anymore. It wouldn't hurt to increase it, but it wouldn't hurt not to.

---

