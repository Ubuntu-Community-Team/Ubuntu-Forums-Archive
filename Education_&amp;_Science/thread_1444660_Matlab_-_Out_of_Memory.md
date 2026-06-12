---
title: "Matlab - Out of Memory"
date: 2010-04-01
forum: Education &amp; Science
---

### Post by naarkhoo on 2010-04-01
I am playing with a huge matrix in Matlab; always face with this error "Out of memory" in matlab environment. 

I think I have to allocate more memory for matlab ... but I don't know exactly how 

here is the out put of "ulimit -a"
> 
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 20
file size               (blocks, -f) unlimited
pending signals                 (-i) 16382
max locked memory       (kbytes, -l) 64
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 16000
cpu time               (seconds, -t) unlimited
max user processes              (-u) unlimited
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

---

### Post by spinoza666 on 2010-04-02
Well, I'm not a matlab user, but I'm sure that if you perhaps include your code and a explanation of what you're trying to do, you are more likely to get some assistance. It might be that your code is consuming more memory than needed, and perhaps a couple of small tweaks to your code will solve your problem.

I'm a R user, and that's usually the case for me.

---

### Post by naarkhoo on 2010-04-03
I trying to make a heatmap plot from 10000*30 matrix ... actually i couldn't and worked on 4000*30 matrix, it still sick and slow ... I don't know who can I allocate more memory space for matlab !!

---

### Post by Naggobot on 2010-04-03
It has been over 10 years since I used Matlab. 10000x30 does not sound too large. If I calculate 30x10000x32 bit / cell I get about 10Mb of memory requirement. Naturally it is not as straight forward with real memory usage but the amount of the memory should not be a problem here in my opinion. I of course may be wrong. 

You should check from the resource monitor if the system is actually low on memory. Also you should check

[http://www.mathworks.com/support/solutions/en/data/1-18150/index.html](http://www.mathworks.com/support/solutions/en/data/1-18150/index.html)

i.e. you should first allocate a continuous space for the Matrix and then populate the matrix with numbers. Also if you are running out of memory then there may be something else in your code that reserves the memory and does not release it before final plotting. I seem to remember that every variable is kept in memory by default and the memory needs to be freed manually.

---

### Post by slaanco on 2010-04-06
is the output of
```

size(array)
```
the same as what you expect to be the size of your array? resp. defined the size of your array before hand with zeros command.

Matlab should not have problems with such array, but maybe its guessing what you want from it and that when the problem is ;)

---

