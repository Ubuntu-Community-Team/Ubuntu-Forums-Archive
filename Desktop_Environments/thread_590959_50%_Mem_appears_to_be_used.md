---
title: "50% Mem appears to be used"
date: 2007-10-25
forum: Desktop Environments
---

### Post by El Ed on 2007-10-25
Hi,

This may be a bit of a newbie question. I have just upgraded to gutsy, and was under the impression that things were going a bit slower, so I used "top" and saw that my ram was being fully used although I wasn't doing anything particularly demanding (amarok, firefox and thunderbird). I closed everything down and used "top" again and found that more than 50% of the ram was being used. "ps aux" showed that only ~10% of the ram should be taken. 
Is this some bug or is this to be expected? 

Thanks,
Ed

---

### Post by OoooMatron on 2007-10-25
Linux isn't windows. Free RAM is wasted ram so it is used and managed accordingly. that said it is possible you have a memory leak or something causing the slowness but I can't tell.

If gutsy is slow it is being caused by something else but what I don't know.

---

### Post by FredB on 2007-10-25
> **OoooMatron said:**
> Linux isn't windows. Free RAM is wasted ram so it is used and managed accordingly. that said it is possible you have a memory leak or something causing the slowness but I can't tell.

If gutsy is slow it is being caused by something else but what I don't know.

Tracker daemon could be guilty here.  Tracker is the new smart search tool.

Linux on start take all the ram and give ram to programs and processes when needed.

---

### Post by cuby on 2007-10-25
type "top" in the terminal and check the responsible.

If you have an nvidea card with compiz enabled, it can be because of a probable nvidea bug, see:

[http://ubuntuforums.org/showthread.php?t=579739&page=2](http://ubuntuforums.org/showthread.php?t=579739&page=2)

and

[https://bugs.launchpad.net/ubuntu/+s...iz/+bug/151168](https://bugs.launchpad.net/ubuntu/+s...iz/+bug/151168)

---

### Post by El Ed on 2007-10-25
I don't have compiz enabled. 

By looking at top right now:


top - 15:15:26 up 1 day,  5:50,  3 users,  load average: 0.26, 0.20, 0.09
Tasks: 130 total,   2 running, 128 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.3%us,  1.8%sy,  0.0%ni, 91.8%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    [COLOR="DarkOrange"]507532k total,   465468k used[/COLOR],    42064k free,    19092k buffers
Swap:   987956k total,   169360k used,   818596k free,   161940k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                        
 6623 edward    15   0 82360 9736 6836 R   12  1.9   0:06.62 gnome-terminal                                                 
 5449 root      15   0  390m  59m 4368 S    2 12.0  14:27.65 Xorg                                                           
13558 edward    15   0  239m 119m  31m S    2 24.0   5:26.60 firefox-bin                                                    
    1 root      18   0  2952  392  344 S    0  0.1   0:01.41 init                                                           
    2 root      11  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                       
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                        

etc ...

With ps aux it also looks like only 40% should be used.
Could there be processes that do not appear on ps aux that are using the RAM or do I have a mem leak?

Ed

---

### Post by deserthowler on 2007-10-25
> **El Ed said:**
>  With ps aux it also looks like only 40% should be used.
Could there be processes that do not appear on ps aux that are using the RAM or do I have a mem leak? Ed

Did you consider the buffers and caches?

I just ran 'free -m'

I have 2018 MB memory right now being used on my machine.  1035 is being used.  Buffers/cache is 392.  That's about 40% of the total memory being used.

Earl

---

### Post by Glowing Fish on 2007-10-26
I think that buffers are probably the culprit here. What the OS is doing is taking information on harddrive and writing it to memory, in case it is needed. It is the opposite of virtual memory. 

Try to open a few programs, and see if the amount of memory used changes. If it doesn't, that just means that Ubuntu was keeping some information on the harddrive in memory, and now is keeping different, more important information in memory. Also, look at your load averages. If there is really a problem with memory, those will typically start to climb. But as long as they are safely under 1, it shouldn't be a problem.

---

