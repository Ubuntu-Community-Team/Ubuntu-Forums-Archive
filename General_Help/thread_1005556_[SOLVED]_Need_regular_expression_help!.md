---
title: "[SOLVED] Need regular expression help!"
date: 2008-12-08
forum: General Help
---

### Post by magnus0 on 2008-12-08
The command sensors outputs this data:

```
lm85-i2c-0-2e
Adapter: SMBus I801 adapter at c800
V1.5:        +1.48 V  (min =  +0.00 V, max =  +3.32 V)   
VCore:       +1.21 V  (min =  +0.00 V, max =  +2.99 V)   
V3.3:        +3.30 V  (min =  +0.00 V, max =  +4.38 V)   
V5:          +5.10 V  (min =  +0.00 V, max =  +6.64 V)   
V12:        +12.00 V  (min =  +0.00 V, max = +15.94 V)   
CPU_Fan:    1358 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
fan4:        804 RPM  (min =    0 RPM)
CPU Temp:    +58.0°C  (low  = -127.0°C, high = +127.0°C)  
Board Temp:  +48.0°C  (low  = -127.0°C, high = +127.0°C)  
Remote Temp: +47.0°C  (low  = -127.0°C, high = +127.0°C)  
cpu0_vid:   +1.088 V
```

What is the regex for displaying only the CPU Temp number? Like 58.0°C

This is what I wrote myself, but it didn't work:

```
sensors | grep '[CPU Temp +0-90-9.0-9°C]'
```

---

### Post by jgoguen on 2008-12-08
Regex not required:

```
sensors | grep 'CPU Temp' | awk '{print $3};'
```

Unless you want literally only the number, then use this:

```
sensors | grep 'CPU Temp' | awk '{print $3};' | sed 's/[^0-9.]//g'
```

---

### Post by magnus0 on 2008-12-08
> **jgoguen said:**
> Regex not required:

```
sensors | grep 'CPU Temp' | awk '{print $3};'
```

Unless you want literally only the number, then use this:

```
sensors | grep 'CPU Temp' | awk '{print $3};' | sed 's/[^0-9.]//g'
```

Thank you! It works :D

---

### Post by jgoguen on 2008-12-09
Glad to hear this works for you :)  Could you please mark this thread as solved?  Doing so will let other people browsing the forums know that this thread provided a working solution to your problem.  To mark a thread solved, click the **Thread Tools** link just above and to the right of your first post.  A menu will appear; one of the options in there will be to mark the thread as solved.

Thanks :)

---

