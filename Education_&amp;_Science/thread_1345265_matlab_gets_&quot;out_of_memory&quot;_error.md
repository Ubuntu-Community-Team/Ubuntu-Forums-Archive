---
title: "matlab gets &quot;out of memory&quot; error"
date: 2009-12-03
forum: Education &amp; Science
---

### Post by lidengdeng on 2009-12-03
Hi guys:

I am using matlabe to do cluster with kmeans algorithm. The commands are listed as:
>> load ./Data/train.matrix
>> S = spconvert(train);
>> Idx = kmeans(S, 2);

The file train.matrix store the non-zore values of a sparse matrix. The sparse matrix S may have 100,000 rows and 10,000 columns with about 1,000,000 non-zero cells. 

The matlab gets the error of "Out of memory. Type HELP MEMORY for your options.". So how to augment the memory size?

My PC is 32bit with 3G memory, Ubuntu8.04 and Mathworks.Matlab.R2008b.UNIX are installed.

The top -c command shows that MATLAB process only occupies 6.7%MEM.
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND 
16306 ldd       20   0  496m 203m  47m S   98  6.7   2:22.03 /home/ldd/matlab/bin/glnx86/MATLAB 




Any suggestion to fix it? thanks.

---

### Post by pvonbert on 2009-12-03
It is indeed a memory problem. Try clearing all non essential data from memory, using 
>> clear train
or
>> keep S
and run again. Could you divide and conquer if this fails using parts of the data?
Check the help on data types, use single instead of double precision.
try also
>> help memory
it will show a few more tips

---

### Post by lidengdeng on 2009-12-04
> **pvonbert said:**
> It is indeed a memory problem. Try clearing all non essential data from memory, using 
>> clear train
or
>> keep S
and run again. Could you divide and conquer if this fails using parts of the data?
Check the help on data types, use single instead of double precision.
try also
>> help memory
it will show a few more tips

Thanks for yr suggestion.

Though i use "clear train" before running kmeans, the error remains there.
It's weird that commands of "keep S" and "memory" are illegal in my platform.

I am transferring the program into a 64-bit pc and help that works.

---

### Post by pvonbert on 2009-12-04
Hi lidengdeng, sorry for the delay, but work trumps you, I guess.

The latest version I have is MATLAB Version 7.5.0.342 (R2007b), but since Matlab 4 it has the same help feature. Try doc memory and look under "Memory Allocation in MATLAB". 
The other problem might be if you have a student version of matlab, there are limitations on the array (matrix) size.

As I understand, you get the Out of memory message when you run
>> Idx = kmeans(S, 2);
It means there is no contiguous space in the memory to allocate space for Idx. Do
>> clear train; pack 
and watch what is the memory release from Matlab (using top or htop).
run again the
>> Idx = kmeans(S, 2);
if you get the memory error again, save your S sparse matrix and restart Matlab. This way you will load S w/o the intermediate step.

Also you should realize that "IDX = kmeans(X,k) partitions the points in the n-by-p data matrix X into k clusters". So IDX might be to large anyway. I've never used kmeans, but it is an iterative process, and might run out of memory because it uses and releases memory, and this way it will run out of contiguous space. As I said last night, divide .... , 

The 'keep' is one of the goodies available for free at the Matlab Central web site.

If all else fails, did you try 'R'?, K-Means Clustering
[http://www.stat.ucl.ac.be/ISdidactique/Rhelp/library/mva/html/kmeans.html](http://www.stat.ucl.ac.be/ISdidactique/Rhelp/library/mva/html/kmeans.html)
can be run with less iterations, or it just might be that it uses a different algorithm and is best suited to your very large data set.

Hope some of this helps ....
p

---

