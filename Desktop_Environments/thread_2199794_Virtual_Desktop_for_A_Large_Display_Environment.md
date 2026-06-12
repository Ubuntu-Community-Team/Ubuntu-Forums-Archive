---
title: "Virtual Desktop for A Large Display Environment"
date: 2014-01-15
forum: Desktop Environments
---

### Post by leaf-nick on 2014-01-15
Hello all. I have a large display wall at my disposal, and I'd like some way to have a unified desktop environment for it. I've looked at some existing software that is supposed to solve this problem (e.g. SAGE), but haven't had much luck.

The wall consists of 16 individual displays. Four displays are connected to each of four computers (2 GPUs per computer), with one additional computer that acts as the head node. My initial thought is that the head node could render to an 8k x 4k virtual monitor, and the resultant image could be quartered and sent to the appropriate set of displays. This is a bandwidth-intensive approach, but the 5 computers in the cluster are on a fast local network.

To me, this sounds simple to implement, and I'm comfortable with C/C++, OpenGL, and MPI (what I would probably use for distributing the sub-images). My main issue is that I don't know where to begin looking to insert the code that would create, divide, and distribute a virtual monitor. Does anyone have any advice on where I should start looking?

Thanks!

---

