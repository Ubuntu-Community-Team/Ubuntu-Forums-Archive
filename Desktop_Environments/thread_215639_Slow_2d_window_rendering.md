---
title: "Slow 2d window rendering"
date: 2006-07-14
forum: Desktop Environments
---

### Post by Bezvardis on 2006-07-14
I am trying to solve the window rendering problem but cannot find solution. 
Problem: when more than one window is open or even with one Firefox window open, when I move it around it renders really slow. In some cases the window gets smeared all over the screen for a second or two until it finally sets as it should. 

I have an nVidia TNT2 Riva card and an older computer (AMD 700 Mhz). I recently installed the nVidia legacy drivers and since then the 3D screensavers are performing well, but the window rendering still gets on my nerves. I thought maybe someone can suggest me of something. Have been looking around the forums but cannot find anything useful.

Thanks.

---

### Post by Teroedni on 2006-07-14
are you low on memory

That could leed to swapping which is extremely painfull

what does 
```
cat /proc/meminfo
```
return


and what does ```
cat /proc/swaps

``` returns

---

### Post by Bezvardis on 2006-07-14
Here are the returns:


```

:~$ cat /proc/meminfo
MemTotal:       256244 kB
MemFree:          3060 kB
Buffers:          5324 kB
Cached:          94788 kB
SwapCached:      13904 kB
Active:         166036 kB
Inactive:        62756 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       256244 kB
LowFree:          3060 kB
SwapTotal:      224868 kB
SwapFree:       210964 kB
Dirty:             608 kB
Writeback:           0 kB
Mapped:         156708 kB
Slab:            13136 kB
CommitLimit:    352988 kB
Committed_AS:   278412 kB
PageTables:       1720 kB
VmallocTotal:   770040 kB
VmallocUsed:     25408 kB
VmallocChunk:   743412 kB

```


```
 cat /proc/swaps
Filename                                Type            Size    Used    Priority/dev/hda5                               
partition       224868  18820   -1


```

Although I don't understand much of what is above, it did not seem there would be much swapping (judged by the disk activity)

---

### Post by Teroedni on 2006-07-14
try with 

```
sudo swapoff /dev/hda5
```


Does it yield any difference?

---

### Post by Bezvardis on 2006-07-14
> **Teroedni said:**
> try with 


Does it yield any difference?

same thing as previously

---

