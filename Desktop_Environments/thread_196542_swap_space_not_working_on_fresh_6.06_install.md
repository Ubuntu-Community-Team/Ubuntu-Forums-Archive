---
title: "swap space not working on fresh 6.06 install"
date: 2006-06-14
forum: Desktop Environments
---

### Post by zaparo on 2006-06-14
Swap wasn't set up properly by the installer (alternate disc).  This is on a desktop machine and I'm not using hibernation.  I even tried deleting the swap partition, recreating it and rebooting with no luck.

Relevant information:

```
root@zaparo:~# free -m
             total       used       free     shared    buffers     cached
Mem:           249        247          2          0         67         56
-/+ buffers/cache:        122        126
Swap:            0          0          0
root@zaparo:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
root@zaparo:~# swapoff -a
root@zaparo:~# mkswap -c /dev/hda1
Setting up swapspace version 1, size = 1003446 kB
no label, UUID=6eadb75e-cf86-42f0-9529-c1faf8890d77
root@zaparo:~# swapon -a
swapon: /dev/hda1: Invalid argument
root@zaparo:~#
```

---

### Post by ape on 2006-06-14
What partition type is /dev/hda1 set to?  Swap partitions should be set as type 82(LINUX_SWAP).

Also, do you get the same "Invalid Argument" if you try `swapon -v /dev/hda1`?

--Ape--

---

### Post by jsc1328 on 2006-06-14
Hi,

Could we see the result of 'fdisk -l'?

\J

---

### Post by zaparo on 2006-06-14
Results from fdisk:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         122      979933+  82  Linux swap / Solaris
/dev/hda2   *         123        3648    28322595   83  Linux

```

---

### Post by zaparo on 2006-06-14
[QUOTE=ape]What partition type is /dev/hda1 set to?  Swap partitions should be set as type 82(LINUX_SWAP).

Also, do you get the same "Invalid Argument" if you try `swapon -v /dev/hda1`?

--Ape--[/QUOTE]

No luck:

```
root@zaparo:~# swapoff -a
root@zaparo:~# mkswap -c /dev/hda1
Setting up swapspace version 1, size = 1003446 kB
no label, UUID=71f01fa1-9fdf-45cc-a4c9-94ef22840f59
root@zaparo:~# swapon -v /dev/hda1
swapon on /dev/hda1
swapon: /dev/hda1: Invalid argument
root@zaparo:~#
```

---

### Post by zacbarton on 2006-06-14
I had the same problem

I updated my fstab entry to
```
/dev/sdb3       swap                 swap       pri=42                0 0
```

Then did
```

swapoff -a
swapon -a
```

After that I could see the swap in the system monitor.
I think changing the mount point from none to swap was the key.

I found more info here [http://www.cyberciti.biz/tips/performance-tuning-for-linux-swap-partition.html](http://www.cyberciti.biz/tips/performance-tuning-for-linux-swap-partition.html)

---

### Post by vasimakhtar on 2006-06-14
Hi,
I found the same problem with my PC. But now relaxed. Please read the following, which I found from Google.

A lot of Linux newbies, myself included are often astonished at the amount (%) of memory used by Linux as opposed to, say, Windows on comparable systems. If you look at the System Monitor (Applications -> System Tools -> System Monitor), you can find the amount of memory used by your system. If you leave your computer on for a long period (say more than a day) then the memory usage seems to keep going up. This is a “good thing”. Let me explain why.

Linux actively uses free available memory to improve your system’s performance. Let’s say you have 1 GB of main memory (don’t we all wish!). Now, suppose all the programs you are running together require only 200 MB of memory. What happens to the other 800 MB of the available memory? 

On a linux system, the memory is used to “cache” data that is used by the CPU. The idea behind caching is that it takes longer for your CPU to access data on the hard drive than it does to access data that is present in the main memory. So caching using the main memory effectively speeds up the system. On a windows system, there is no such optimization, so free memory is wasted as it does not get used.

Now when an application really needs all the memory that is used for caching, Linux pops out the cached data and makes the required memory available. As a last option, if all of the main memory is used up, then the memory you set aside in your swap partition is used too.

Try the command:
$free -m

to see what your memory usage is. The first line of results is fairly obvious. The second line tells you what the applications “see”, and should tell you how much memory is actually being used by the applications themselves.

Another used command is “top” which gives you a look at the memory/cpu usage and other details about the processes that are running on your computer - all at the terminal. I much prefer it to the GUI-based System Monitor myself.

Knowing that all the memory I paid for is being used to the max makes me feel all warm and fuzzy. For a moment earlier today, I thought there was something wrong, since almost all of my memory was being used, and I was hardly running anything intensive - now I am at ease - there was something wrong earlier, when the memory was not being used by Windows - now I know!!

---

### Post by zaparo on 2006-06-16
[QUOTE=zacbarton]
I updated my fstab entry to
```
/dev/sdb3       swap                 swap       pri=42                0 0
```
[/QUOTE]

No luck, again.

---

### Post by zaparo on 2006-06-16
[QUOTE=vasimakhtar]Hi,
I found the same problem with my PC. But now relaxed. Please read the following, which I found from Google.

...
[/QUOTE]

Is this spam?  Are you serious?  This has nothing, whatsoever to do with my question.

---

