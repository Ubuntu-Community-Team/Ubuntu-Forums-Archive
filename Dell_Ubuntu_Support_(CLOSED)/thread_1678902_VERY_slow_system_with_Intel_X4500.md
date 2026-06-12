---
title: "VERY slow system with Intel X4500"
date: 2011-01-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mvalo on 2011-01-31
Hi,

I have Dell Latitude E6400 with Intel X4500 GPU on Ubuntu 10.04. I am using external monitor with 1920x1080 resolution (which is already maximum resolution). I have serious speed problems after some time of watching videos (not HD, but DVD quality), of using flash (e.g. youtube). System is VERY slow, opening gedit takes minutes, shuting down system correctly is almost impossible. CPU is constantly working on 100%. It seems that system is overheaten. 

It is problem of HW (GPU) or can it be considered as bug?

Matus

---

### Post by mikewhatever on 2011-02-01
It could be any of the above and a couple of other things. Something seems to overload the system, and you'd have to figure out which process that is. Use the system monitor or htop to see which process utilizes cpu the most. Looking at memory usage with the system monitor or 'free -m' might also help.

---

