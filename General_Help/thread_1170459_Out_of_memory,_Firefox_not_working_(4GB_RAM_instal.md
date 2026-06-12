---
title: "Out of memory, Firefox not working (4GB RAM installed)"
date: 2009-05-26
forum: General Help
---

### Post by MountainX on 2009-05-26
I'm running Jaunty on a desktop with 4GB of RAM. It has been up for 7 days and I am using Firefox a lot. But now Firefox has started misbehaving. For example, it will not download (open) a PDF file. So I looked at system monitor and all my RAM is used (nearly 100% used and only 5% of that is cache).

So I closed all apps, logged out and logged back in and still my 77% used by programs and 16% used by cache. After logging back in, below are some stats I see.

My questions are:
1. how can I clear (free up) some memory without rebooting?
2. how can I prevent this problem in the future? (Maybe use a swap partition?)

```
$ free
             total       used       free     shared    buffers     cached
Mem:       3989648    3908632      81016          0      53680     572876
-/+ buffers/cache:    3282076     707572
Swap:            0          0          0

$ vmstat
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  0      0  85016  53588 571068    0    0     1     8   22   23 12  4 83  0

$ iostat
Linux 2.6.28-11-generic (MyDesktop)     05/26/2009     _x86_64_    (2 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          11.98    0.28    4.49    0.06    0.00   83.33

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda               1.83         4.06        34.17    2790875   23515042
sda1              1.83         4.03        34.17    2773918   23515024
sda2              0.00         0.01         0.00       9492         10
sda3              0.00         0.00         0.00       1098          0
sda4              0.00         0.01         0.00       6023          8
dm-0              4.45         4.03        34.17    2772714   23515024
sdb               0.00         0.01         0.00       6338          2
sdb1              0.00         0.01         0.00       6106          2
dm-1              4.44         4.02        34.17    2769986   23515024
dm-2              0.01         0.01         0.00       4146          8


```

---

### Post by Legace on 2009-05-26
Type top in Terminal and see which uses RAM.

If you don't have swap, get one.. That is probably causing the problem..

---

### Post by MountainX on 2009-05-26
```
top - 11:38:32 up 8 days, 2 min,  4 users,  load average: 1.75, 1.87, 1.57
Tasks: 195 total,   4 running, 191 sleeping,   0 stopped,   0 zombie
Cpu(s): 43.7%us,  5.3%sy,  0.0%ni, 50.3%id,  0.2%wa,  0.3%hi,  0.2%si,  0.0%st
Mem:   3989648k total,  3898436k used,    91212k free,    55524k buffers
Swap:        0k total,        0k used,        0k free,   603004k cached
```

Is there a way to free up some memory without rebooting? The above is after logging out and back in and now I have almost no applications open (compared to before when I had about 50 web pages open in Firefox).

---

### Post by philinux on 2009-05-26
> **MountainX said:**
> ```
top - 11:38:32 up 8 days, 2 min,  4 users,  load average: 1.75, 1.87, 1.57
Tasks: 195 total,   4 running, 191 sleeping,   0 stopped,   0 zombie
Cpu(s): 43.7%us,  5.3%sy,  0.0%ni, 50.3%id,  0.2%wa,  0.3%hi,  0.2%si,  0.0%st
Mem:   3989648k total,  3898436k used,    91212k free,    55524k buffers
Swap:        0k total,        0k used,        0k free,   603004k cached
```

Is there a way to free up some memory without rebooting? The above is after logging out and back in and now I have almost no applications open (compared to before when I had about 50 web pages open in Firefox).

It could be an app you used over the seven days had a memory leak. I'd reboot.
But before that I'd do a 
killall firefox and check acroread is not running.
By the way if you using acroread then that is the problem app that causes the processor and memory problems. I've uninstalled mozillla-acroread.

---

### Post by MountainX on 2009-05-26
> **philinux said:**
> It could be an app you used over the seven days had a memory leak. I'd reboot.
But before that I'd do a 
killall firefox and check acroread is not running.
By the way if you using acroread then that is the problem app that causes the processor and memory problems. I've uninstalled mozillla-acroread.

I do have acroread installed and I've used it a lot recently. What do you use instead?
I think Firefox leaks memory. (But maybe it is a FF add-on instead.)

I'll kill firefox after I send this message :)

Thanks

---

### Post by artsci2 on 2009-05-26
I have this out of memory problem from tome to time when I leave firefox open and let the computer go into it's screensaver. After a few hours If I wake it back up it will have full memory and swap used when before it has less than 1Gb used and never touched swap. It's like something eats away at the memory while the computer is sleeping.

---

### Post by MountainX on 2009-05-26
top shows the process using the most memory is this:
```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
21755 root      20   0  499m 346m 1752 S    5  8.9 148:24.20 gvfs-fuse-daemo 
```And here is the memory summary with Firefox closed and nothing but a couple terminal windows open (and not much of anything has been opened since I logged out and back in)

```
Mem:   3989648k total,  3271508k used,   718140k free,    51088k buffers
```Now, I ran this command:```

# echo 3 > /proc/sys/vm/drop_caches
```source: [http://www.ubuntu-unleashed.com/2008/04/free-up-cache-memory-in-linux.html](http://www.ubuntu-unleashed.com/2008/04/free-up-cache-memory-in-linux.html)
(I ran sync before doing that just to be safe. Sync didn't change the memory used.)

Here's the memory summary after running that (and with Firefox, terminals open):
```
Mem:   3989648k total,  1088620k used,  2901028k free,     1140k buffers
```That looks similar to what it would be an hour or so after rebooting... so I think I'm satisfied now :)

---

### Post by deadlockedgamer on 2009-05-26
Though i have never experienced it I have heard of a similar issue in windows but it only required a restart of firefox. Never had an issue in ubuntu with it either.

---

### Post by MountainX on 2009-05-26
> **deadlockedgamer said:**
> Though i have never experienced it I have heard of a similar issue in windows but it only required a restart of firefox. Never had an issue in ubuntu with it either.

I have heard that some screen savers have memory leaks. I never turn my computer off and Firefox is usually open 24 x 7. So I think I will turn my screen saver off.

Anyway, I never rebooted and I have plenty of free memory now and everything is working. Ubuntu is great :)

---

### Post by philinux on 2009-05-26
> **MountainX said:**
> I do have acroread installed and I've used it a lot recently. What do you use instead?
I think Firefox leaks memory. (But maybe it is a FF add-on instead.)

I'll kill firefox after I send this message :)

Thanks

In preferences change pdf opening to the default Document Viewer. Then when clicking a pdf link it downloads and opens Evince. No more memory full or cpu 100%.

---

### Post by danwood76 on 2009-05-26
Yeah evince is better than adobe acrobat reader. (odd as pdf is adobes creation)
I've only encountered one pdf that evince wouldnt open, and then I still have acrobat as a backup. I've always had memory and CPU issues with adobe acrobat reader so I just stear clear of it!

---

