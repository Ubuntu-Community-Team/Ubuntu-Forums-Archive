---
title: "Memory Problem"
date: 2006-06-14
forum: Desktop Environments
---

### Post by vasimakhtar on 2006-06-14
Hi,
I just check memory through "free-m" command and it gives me following results

vasimakhtar@vasimakhtar:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           249        244          5          0          3         77
-/+ buffers/cache:        162         86
Swap:          729         18        710


It says I have only 5 free space. Does it matter with the performance of PC. What should I do to increase that? Any help?
thanks

---

### Post by vasimakhtar on 2006-06-14
Hi,
I found reply for the same. Please read hereunder:

A lot of Linux newbies, myself included are often astonished at the amount (%) of memory used by Linux as opposed to, say, Windows on comparable systems. If you look at the System Monitor (Applications -> System Tools -> System Monitor), you can find the amount of memory used by your system. If you leave your computer on for a long period (say more than a day) then the memory usage seems to keep going up. This is a “good thing”. Let me explain why.

Linux actively uses free available memory to improve your system’s performance. Let’s say you have 1 GB of main memory (don’t we all wish!). Now, suppose all the programs you are running together require only 200 MB of memory. What happens to the other 800 MB of the available memory? 

On a linux system, the memory is used to “cache” data that is used by the CPU. The idea behind caching is that it takes longer for your CPU to access data on the hard drive than it does to access data that is present in the main memory. So caching using the main memory effectively speeds up the system. On a windows system, there is no such optimization, so free memory is wasted as it does not get used.

Now when an application really needs all the memory that is used for caching, Linux pops out the cached data and makes the required memory available. As a last option, if all of the main memory is used up, then the memory you set aside in your swap partition is used too.

Try the command:
$free -m

to see what your memory usage is. The first line of results is fairly obvious. The second line tells you what the applications “see”, and should tell you how much memory is actually being used by the applications themselves.

Another used command is “top” which gives you a look at the memory/cpu usage and other details about the processes that are running on your computer - all at the terminal. I much prefer it to the GUI-based System Monitor myself.

Knowing that all the memory I paid for is being used to the max makes me feel all warm and fuzzy. For a moment earlier today, I thought there was something wrong, since almost all of my memory was being used, and I was hardly running anything intensive - now I am at ease - there was something wrong earlier, when the memory was not being used by Windows - now I know!!

Thanks

---

