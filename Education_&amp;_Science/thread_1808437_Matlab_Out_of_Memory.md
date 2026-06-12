---
title: "Matlab: Out of Memory"
date: 2011-07-20
forum: Education &amp; Science
---

### Post by evenrelation on 2011-07-20
Hello all

I hope there is someone who can give me some pointers. 

I have a program in Matlab (R2010a) running on 32 bit Ubuntu 11.04, memory is 2.7 Gb and 7.9 Gb Swap. Almost immediately after I run the code, I get out of memory error. 

In the System Monitor, the Swap is unused during the execution. Isn't that exactly what should be utilized in situations like this?

```
             total       used       free     shared    buffers     cached
Mem:       2835688    1261540    1574148          0      99904     507744
-/+ buffers/cache:     653892    2181796
Swap:      8313600         96    8313504
```I am pretty sure my code is correct.

Take note that I have very little idea on how memory works.

---

### Post by tommpogg on 2011-07-21
Me too I am not a "memory expert". But I am quite familiar with Matlab.

You can try to check the following
1) Are you using a variable which size is too big? In this case, figure out if you can write your code using "for" cycles; the execution speed will decrease but the code will run.
2) Can you write your code in order to use a sparse matrix formulation? It really helps with memory problems.

I am not sure, but I believe that Matlab is not allowed to use all the memory.
Anyway, getting memory problems with Matlab is quite common. It seems that it doesn't handle the memory in an efficient way.

---

### Post by evenrelation on 2011-07-21
The variable causing the trouble is as short as possible, and sparse matrix formulation is not possible, unfortunately.

It's a wee bit frustrating having all this memory and not being able to use it.

---

### Post by zgornel on 2011-08-03
The 32-bit version of Matlab has certain memory limits for individual arrays (around ~1.5GB) and all arrays (a bit bigger). So, even though theoretically it could use more (up to 4GB), the implementation forbids it. The 64-bit version should work well up to 8TB so, if you need a lot of memory, 32-bit is a bad choice. 

A solution you could try is to save parts (that are not needed) of your variable to disk, reduce the variable to a smaller size (clearing the saved parts) and so on ...

---

### Post by JCM_Pico on 2011-08-05
You are probably loading a large matrix, and you don't have enough memory for it.
Will you run your script keep an eye on System Monitor and check out the memory behaviour.
Other way you could try is to place a return in your script and run it in some little pieces at time. In that way you are capable of identify the variable that's causing the out of memory...

One thing to have in mind is that Matlab will not use your swap....

---

### Post by dankdave on 2012-05-01
Try executing your program with the Matlab debugger turned on.  It should give you a stack trace of where it ran out of memory.

How large is your matrix?

---

