---
title: "Plasmashell using 99% of CPU"
date: 2019-02-15
forum: Desktop Environments
---

### Post by oygle on 2019-02-15
Computer running very slow. I thought it was 'baloo' so cancelled that, but still slow..

Plasmashell using 99% of CPU.

---

### Post by oygle on 2019-02-15
This states it is fixed, but it is not fixed - [https://bugs.kde.org/show_bug.cgi?id=356479](https://bugs.kde.org/show_bug.cgi?id=356479)

This fixed it, down to  less than 1% now, but why does it happen ?

```
killall plasmashell; kstart plasmashell; exit

```

Some posts stated it was an animated widget that pushes the CPU usage up. I did have an animated notification for a file copy, but why does it stay at 99%

Anyway, there is a work around, but it is definitely still a bug.

---

### Post by QIII on 2019-02-15
Hello!

The bug probably is fixed.  It is certainly not happening on my machine.  But that doesn't mean you can't be having the problem, of course.

Would you please provide the output of 

```
top
```

or

```
htop
```

so we can find a place to start?

---

### Post by oygle on 2019-02-16
> **QIII said:**
> ..... 

so we can find a place to start?

Thanks for your reply. It's not 99% now, but less than 1%, so the terminal command got it fixed. I will hopefully remember to run those commands for you if the problem appears again.

Thanks :)

---

### Post by oygle on 2019-02-16
Well, I thought it would be weeks or months before it happened again, but it just happened about 15 minutes ago.

I had claws open and opened Firefox. The screen response was nothing, so looked at KSysGuard and sure enough plasmashell was using 100% CPU, so ran **top**.

[ATTACH=CONFIG]282536[/ATTACH]

---

### Post by oygle on 2019-02-16
Running **top** and **baloo_file_extr** is using 100% CPU. Do I really need **baloo** ? It has always been resource hungry.

... and now **plasmashell** is using 100% CPU.  :(

I need to file this as a bug, .. ridiculous.

---

### Post by QIII on 2019-02-16
Go ahead and send a bug report, but I don't see any of that happening on my machine and I don't see anyone else asking for help with it.

I disable baloo and a the kde default services.

---

### Post by CatKiller on 2019-02-16
> **oygle said:**
> Do I really need **baloo** ? 

No.

For me, it crashed whenever a new file was created. It's easy to disable, and nothing bad happens if you disable it.

---

### Post by oygle on 2019-02-16
> **QIII said:**
> Go ahead and send a bug report, but I don't see any of that happening on my machine and I don't see anyone else asking for help with it.

I'll hold off on the bug report. It does still seem a problem as a Google search on 'plasmashell is using 100% CPU' showed many instances. I may try some of those fixes shown, but the obvious question is, why did it start to become a problem. I'll look into disabling the widget/notifications,as it seems that is what can potentially initiate the high CPU usage from plasmashell.

> **QIII said:**
> 
I disable baloo and a the kde default services.

Thanks, this article seems ok - [https://medium.com/@alexadam/disable-baloo-file-extractor-kubuntu-17-04-3f84f7dddb70](https://medium.com/@alexadam/disable-baloo-file-extractor-kubuntu-17-04-3f84f7dddb70)

> **CatKiller said:**
> No.

For me, it crashed whenever a new file was created. It's easy to disable, and nothing bad happens if you disable it.

Thanks.

---

### Post by oygle on 2019-06-19
After killing plasmashell and baloo, CPU is back to normal, however cannot do a "Print Screen" with the **PrtScr **key. It usually works fine.

---

