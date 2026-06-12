---
title: "Confusion!!!!!"
date: 2006-08-24
forum: Desktop Environments
---

### Post by soutSA on 2006-08-24
Hello,

I've got the following graphics controller in my Sony Vaio:

Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller

I also got 512mb RAM

I am experiencing some slow refresh rates and my xine has started dropping frames. This all happened one day and so far I am unable to troubleshoot what the problem is. I have read in one of the threads that firefox is taking up huge amounts of memory. Also if you use the following command you see that most of the memory is being used.

```
free -m
```
[HTML]             total       used       free     shared    buffers     cached
Mem:           494        485          8          0          1        112
-/+ buffers/cache:        370        123
Swap:         1443         18       1424[/HTML]

I have also installed  xorg-aiglx + compiz yesterday and that was running fine untill this morning. Is there a way to see what is eating my memory or to troubleshoot my graphics controller?

Thanks in advance

---

### Post by skcoyote on 2006-08-25
Try ```
ps aux --sort=rss
```

That will give you a list of all running processes on your system, sorted in increasing order of the amount of resident memory they are consuming. In other words, the most memory-hungry applications will appear at the end of the output.

If you suspect firefox specifically, try ```
ps aux | grep -i firefox
```... or don't run Firefox, and see if your problem disappears.

See also top(1). Running "top" will show you a list of all running processes, with some useful system-level statistics at the top. The process list here is sorted in decreasing order of CPU usage over the polling period (3 seconds by default). Look for the same process(es) near the top of the list *consistently* consuming a double-digit CPU percentage--it may be imposing a performance hit on your system.

Finally, it's still possible that your system is doing something IO bound that is robbing interrupts or bus bandwidth, and it's also possible that you just have a buggy graphics adapter or driver. I don't know anything about the chipset you mentioned, unfortunately... so general troubleshooting advice is all I can give.

Hope this helps!

---

