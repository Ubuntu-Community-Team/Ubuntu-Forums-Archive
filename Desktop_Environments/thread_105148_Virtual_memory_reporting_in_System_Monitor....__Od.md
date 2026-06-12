---
title: "Virtual memory reporting in System Monitor....  Odd!"
date: 2005-12-17
forum: Desktop Environments
---

### Post by musther on 2005-12-17
Ok, maybe this is just me being silly (again).

I added up the figures in the virtual memory column of the system monitor in Ubuntu 5.10  I got a rough figure of 850MiB (rounding down).  According to the 'Resources' tab, I've only used about 250MiB of my RAM, and my swap isn't being used at all (nor should it be, I have 2g of RAM).

So, is this just allocated memory, ie memory the processes are allowed to use, or is something just a little off?

---

### Post by soulestream on 2005-12-17
linux allocates RAM, but doesnt use it till it needs too.

soule

---

### Post by Hallavej on 2005-12-20
I was wondering about it too. And I still dont get it. Can it really allocate more memory that I have, and if so why?. When I add it all up I get more that about 2.5Gb. I have 512 mb ram and 1Gb swap. 
And what about "top". Does that show the "real" memory use?

---

### Post by CarVac on 2008-04-04
I have the same "problem." I use Folding@home, and right now according to the tray applet, 55% of my 2 gigs of ram is used by programs and 27% as cache. The ram usage I don't feel like verifying (adding up 50 list values is annoying), but the weird part is my virtual memory usage is sky-high. Xorg is "using" 917 MiB, Pidgin (why!?!?) is using 426, etc. There are 23 entries with greater than 200 MiB of virtual memory used. What is really weird, though, is my swap is empty. I figure that virtual memory includes files on the hard disk that the programs might use.

---

