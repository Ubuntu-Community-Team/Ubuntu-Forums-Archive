---
title: "Strange memory usage"
date: 2009-01-22
forum: General Help
---

### Post by _jj on 2009-01-22
Ironing out problems in a completely fresh install of Intrepid.
My computer seems very sluggish.  While running some programs for my wory I noticed this as the output to top, despite the RAM memory running at almost 100% effectively no SWAP memory is being used, why is this?
In fact I am running conky and have never seen the swap % move from 0%  Initially I though that this was just an error with conky but on running top I am not so sure.

Example of top output while running a fairly intensive program I wrote
Mem:   1031796k total,   958548k used,    73248k free,    64252k buffers
Swap:  2000052k total,     4692k used,  1995360k free,   382768k cached

Thanks in advance for the help!

---

### Post by stefangr1 on 2009-01-22
This is because swapping is slow. If the system has enough RAM for the processes that are running (and your system has enough, it has still a considerable amount of space left for caching), the swap space will not be used generally.

---

### Post by _jj on 2009-01-22
Ok, this was just a desperate hope that maybe it was a swap problem causing the sluggishness rather than my ancient computer!

---

