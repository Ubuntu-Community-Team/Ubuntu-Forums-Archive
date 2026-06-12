---
title: "Question About Drivers/slow Firefox Speed"
date: 2009-02-02
forum: General Help
---

### Post by sports fan Matt on 2009-02-02
I am Running a Lenovo IdeaCenter K Series K2.3  Pentium dual-core E2180(2.00GHz) 3GB DDR2 500GB Intel GMA 3100 Desktop with Ubuntu Linux 8.10 Intrepid Ibex

And It seems that Firefox stalls repeatably on webpages and this forum.  it "waits" for a long time. I bought this machine less then 6 months ago, so im wondering if my drivers need to be updated and how to? Or is it a different issue? Matt

---

### Post by Crafty Kisses on 2009-02-02
While Firefox is running, run this command and post the results here:
```
top
```

---

### Post by sports fan Matt on 2009-02-02
office@office:~$ top

top - 18:27:52 up 2 days,  2:25,  2 users,  load average: 0.15, 0.22, 0.14
Tasks: 125 total,   1 running, 124 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.8%us,  0.2%sy,  0.0%ni, 99.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2063364k total,  1902236k used,   161128k free,   160464k buffers
Swap:  6048432k total,     1724k used,  6046708k free,  1243824k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
28623 root      20   0  420m  45m 9.9m S    3  2.3   6:20.70 Xorg               
28772 office    20   0 65040  30m  14m S    1  1.5   0:33.44 gnome-panel        
31119 office    20   0  233m  92m  27m S    1  4.6   2:56.84 firefox            
31593 office    20   0 21912  13m 5948 S    1  0.7   0:01.86 compiz.real        
31611 office    20   0 77076  22m  12m S    1  1.1   0:01.10 gnome-terminal     
31632 office    20   0  2416 1148  876 R    1  0.1   0:00.16 top                
    1 root      20   0  3056 1900  576 S    0  0.1   0:01.42 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.30 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:08.26 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.72 events/0           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0      
   54 root      15  -5     0    0    0 S    0  0.0   0:00.46 kblockd/0          
   57 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid             
   58 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify

---

### Post by lenzoid on 2009-02-02
You should post that using the code env, so it uses a fixed font.

Try the following: run ** firefox -P** and make a new profile and try it again. this way you find out if the flaw lies in your configuration.

I also have problems with firefox 3.0.5 hogging my cpu but I know that its a problem with my configuration.

Also you could try a different web browser and see if things are the same. If yes, it's a problem with your internet connection

---

