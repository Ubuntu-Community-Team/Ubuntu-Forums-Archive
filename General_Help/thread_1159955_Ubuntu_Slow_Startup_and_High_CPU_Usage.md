---
title: "Ubuntu Slow Startup and High CPU Usage"
date: 2009-05-15
forum: General Help
---

### Post by Propeng on 2009-05-15
[SIZE=2]Hello,

I've been using Ubuntu for a week without any problem.
Today, when I booted Ubuntu, it took a minute to boot not 30 seconds as usual. Also it takes 100% CPU usage for the first 3 minutes, then drops down to 5%.

I haven't done anything new yesterday. (Expect installation of Java) Any idea on what could be causing the problem?

I heard on another thread that I can use /sys/module/processor/parameters/max_cstate, but I get this:
```
/sys/module/processor/parameters/max_cstate: No such file or directory
```[/SIZE][SIZE=2]
[/SIZE]

---

### Post by KhurramM on 2009-05-15
open top or gnome-system-monitor

see which app or process is chewing your resources.

Killing it might help.

Or using an alternative may be a better idea.

Also check if theres no dependency missing issue.

---

### Post by Propeng on 2009-05-15
[SIZE=2]The panel shows that there's 100% CPU usage, but the System Manager window itself shows that it's 25%.
And there are no dependency issues. I also noticed that this issue occurs outside GNOME since it slows down booting and terminals. Or it's not called a terminal?
By the way I'm a newbie - completely. That's my first week in Linux.  
[/SIZE]

---

### Post by kpkeerthi on 2009-05-15
When your CPU peaks to 100%, open a terminal and enter **top**. Press 'q' to quit and post the output here.

---

### Post by Propeng on 2009-05-15
I've noticed that it now goes up to 100% for 5 seconds after GNOME loads, then it drops down to 0%, and back to 25%. But it's still boots slowly.
Anyway I managed to quickly type 'top' while it's 100%. Here's the output:

```
top - 14:03:00 up 2 min,  2 users,  load average: 3.35, 1.32, 0.49
Tasks: 116 total,   3 running, 113 sleeping,   0 stopped,   0 zombie
Cpu(s): 70.0%us, 20.0%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi, 10.0%si,  0.0%st
Mem:   1544240k total,   342040k used,  1202200k free,    17452k buffers
Swap:    16024k total,        0k used,    16024k free,   142352k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3608 root      20   0 60828  28m 8732 R 93.1  1.9   0:04.48 Xorg               
 3879 propeng   20   0 35396  15m  10m S 93.1  1.0   0:01.00 gnome-terminal     
 3900 propeng   20   0  2448 1176  912 R 93.1  0.1   0:00.06 top                
 3800 propeng   20   0 62228  26m 7672 S 46.5  1.8   0:03.72 compiz.real        
    1 root      20   0  3084 1888  564 S  0.0  0.1   0:02.66 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    8 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 kstop/0            
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0      
   10 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 kblockd/0          
   11 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   12 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
   13 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue 
```

---

### Post by Propeng on 2009-05-15
[SIZE=2]Hello,

Thanks for your help. I tried rebooting now, and it worked fine. :D
I had to disable some Startup Applications, such as the update notifier.

Regards,
Propeng
[/SIZE]

---

