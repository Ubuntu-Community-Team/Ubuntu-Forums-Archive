---
title: "memory leak?"
date: 2010-07-20
forum: Desktop Environments
---

### Post by cesera on 2010-07-20
There seems to be a memory leak in my setup somewhere. When I start my machine, it uses about 400Mb of memory, but the time it has been running for three days the memory usage has increased to about 1.3Gb. I have no idea how I could track down what program(s) is/are causing this. Can anyone point me in the right direction.

Thanks

(Using Kubuntu Lucid amd64.)

---

### Post by ankspo71 on 2010-07-20
Hi,
It could be just the way that Linux stores (caches) data in memory. If we run the command 'free -m', the first line will show us how much memory is being used to store (cache) data (which always seems to increase and rarely decrease), and the second line shows us how much of the memory is physically being used by the system. The third line is for swap.

Here is what mine currently looks like: (see screenshot)

Or are you already aware of this?

---

