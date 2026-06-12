---
title: "Memory consumption"
date: 2009-02-09
forum: General Help
---

### Post by darco on 2009-02-09
A little confused here in reading my memory usage. Running TOP I see:

top - 16:44:42 up  6:56,  4 users,  load average: 0.32, 0.51, 0.46
Tasks: 159 total,   4 running, 154 sleeping,   0 stopped,   1 zombie
Cpu(s):  6.7%us,  0.6%sy,  0.0%ni, 92.8%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3985128k total,  2431176k used,  1553952k free,    36632k buffers
Swap:   265064k total,     5496k used,   259568k free,  1808072k cached

Running free -t -m shows:

                   total       used       free     shared    buffers     cached
Mem:          3891       2286       1605          0         34       1765
-/+ buffers/cache:        486       3405
Swap:          258          5        253
Total:        4150       2292       1858

These both show I have 3.8 gigs of memory and 2.2 being used and 1.6gig of free memory. 
System monitor shows 575.1 mb (14.8%) of 3.8 gigs is being used. Also under processess, the biggest mem hog is Firefox eating up 73mb. TOP shows 97 mb for Firefox.
I barely having anything running so where is all this memory going and which process is correct?
Running Linux Min x64
thxs
darco

---

### Post by darco on 2009-02-10
anyone?

---

### Post by Ahadiel on 2009-02-10
> **darco said:**
> Running free -t -m shows:

             total       used       free     shared    buffers     cached
Mem:          3891       2286       1605          0         34       1765
-/+ buffers/cache:        486       3405
Swap:          258          5        253
Total:        4150       2292       1858

It looks like you have 486mb actually being used. (1765 of 2286) is cached.

---

### Post by darco on 2009-02-10
well that does make sense since I just ran free -m and it reports 966 used under buffers/cache and system monitor shows 956mb of memory being used...confusing that for the line of Mem: "used" shows a different amount.
thxs
darco

---

