---
title: "MPlayer problem"
date: 2005-12-19
forum: Desktop Environments
---

### Post by quai_k8 on 2005-12-19
Hi all ... 
I've got a problem with my MPlayer and dunno how to solve it!
When I start MPlayer I got this error :

> 
MPlayer dev-CVS-051219-02:03-4.0.2 (C) 2000-2005 MPlayer Team
CPU: Intel Pentium M Dothan (Family: 6, Stepping: 8 )
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2


Option Creating needs a parameter at line 1


I've tryed to cpompil my own MPlayer (cvs sources & official website), the 
debian package in Multiverse (386, 586 ... 686) but the same error appear
all time !!

THX in advance

---

### Post by stateq2 on 2006-08-01
I'm having the exact same problems....I figured it was a bug that was going to "work itself" out....but I'm surprised no one else seems to notice :(

```

stateq2@stateq2-laptop:~/x$ mplayer
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4/Celeron 4 Northwood; Pentium 4 EE/Xeon Prestonia,Gallatin (Family: 15, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


Option Creating needs a parameter at line 1

```

---

### Post by stateq2 on 2006-08-20
The solution to my problem was to simply delete the ~/.mplayer directory...go figure

---

