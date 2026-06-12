---
title: "Gnome-terminal slow startup Ubuntu 10.10"
date: 2011-01-02
forum: Desktop Environments
---

### Post by Luxman on 2011-01-02
Hello forum!

I recently did a fresh new install of Meerkat and I noticed an extremely slowness of gnome-terminal startup. The output of time is:
```
time gnome-terminal
real	0m4.155s
user	0m0.044s
sys	0m0.020s

```

As you can see it is far to slow to startup. I noticed also a raise of the CPU usage above 50% for few seconds.
Anybaody experienced the same problem? Any workaround?

Thanks a lot and happy 2011 :-)

---

### Post by theasprint on 2011-01-02
Hi,

I am not sure what is the exact cause of the problem.
There may be a few things I would want you to try:

1. Go and type the output of this in terminal. This shows what is the most consuming process etc.
```
top
```

2. Output of this. This shows the free memory you have
```
free -m
```

3. And lastly go and check the Startup Applications.

I may think that something is delaying the gnome-terminal startup. Perhaps some other program?

---

### Post by matt_symes on 2011-01-02
Hi

Do you have anything unusual in .bashrc?

Kind regards

---

### Post by Luxman on 2011-01-02
@theasprint

This is my top output while running a gnome-terminal:

```
 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1818 papageno  20   0  124m  44m  18m S    6  4.4  11:39.05 plugin-containe    
 1723 papageno  20   0 92616  14m  10m S    3  1.4   0:03.36 gnome-terminal     
 1058 root      20   0 61424  19m   9m S    3  1.9   3:18.53 Xorg               
 1757 papageno  20   0  363m 113m  28m S    2 11.4   9:28.84 firefox-bin        
    9 root      20   0     0    0    0 S    0  0.0   0:02.60 events/0           
 1703 papageno  20   0 33944  18m 3940 S    0  1.9   0:23.21 ubuntuone-syncd    
 2381 papageno  20   0  2620 1124  832 R    0  0.1   0:00.03 top                
    1 root      20   0  2888 1652 1192 S    0  0.2   0:00.67 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:01.79 ksoftirqd/0        
    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      20   0     0    0    0 S    0  0.0   0:00.30 ksoftirqd/1        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
   10 root      20   0     0    0    0 S    0  0.0   0:00.86 events/1           
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset            
```

here's the free -m after several hours of computer running (firefox loaded):

```
             total       used       free     shared    buffers     cached
Mem:          1001        853        147          0         73        440
-/+ buffers/cache:        339        661
Swap:         2180          0       2180

```

@matt_symes

I have a fresh install of Meerkat, no changes to the config default files, .bashrc included

---

### Post by theasprint on 2011-01-03
Hi,

Gark, I'm not so sure about this but your system looks like its ok to me. Yes, even the memory is plentiful.

Actually I'm not sure if your output of the "time" command is regarded slow or not.

I mean if I'm not wrong, your gnome-terminal starts at 4 seconds after startup?
I'm not sure how to read the results from the "time" command, in fact its my first time seeing this command. 

If its like 4 seconds then only gnome-terminal starts, I find it ok.

---

### Post by matt_symes on 2011-01-03
Hi

4.5 second is slow and a lot slower than on my install of 10.10. Then again you have 1Gb memory and that is not a huge amount, but i still find it hard that it would take a factor of 10 longer to load on your machine than mine because of the memory (as this is a new default setup).

You could just load it at startup (as part of startup applications) and use screen when you first open the terminal. That way you will not have to open another while the PC is up and running, just create and remove screens as required.

After all, a 4 second startup is not the end of the world. But it is a bit strange...

BTW: Is anything appearing in any of the logs when you start up gnome terminals?

```
tail -f ~/.xsession-errors
```

Kind regards

---

### Post by Luxman on 2011-01-03
No relevant errors on that log file...
I know 1 G RAM is not much... but is more than enough for that purpose.. Plus I didn't get any problems with the previous Ubuntu release (same machine).. I know that 4 secs might sound little time but I guarantee you that to fire up a terminal its eternity...
Thanks for the screen tip, even though I don't like much work-arounds, especially for basic stuff like the gnome terminal.
I'll keep on looking for a solution..
Thanks a lot!!

---

### Post by Luxman on 2011-01-03
I noticed that starting xterm takes much less time, less than a second.. It appears to me a really "gnome-terminal" specific problem in my system :(

---

### Post by Parama on 2011-04-07
> **Luxman said:**
> I noticed that starting xterm takes much less time, less than a second.. It appears to me a really "gnome-terminal" specific problem in my system :(

I have the same problem on my Fujitsu Lifebook E8410 (Core2Duo T9300 2.5GHz, 4GB RAM): *gnome-terminal* takes about 4 secs to start, *xterm* pops up almost before I release <enter> (after typing xterm in the Alt+F2 Run dialog)

---

### Post by Parama on 2011-04-07
I solved my own problem: Open the settings for the *Default* gnome-terminal profile, go to Background tab and uncheck *Use background settings from system theme*, selecting the color option (dunno what it's called in english, but it's not *background image* option nor *transparent background* option).

Hope it helps. 

It seems like a bug but who cares as long as upcoming Natty doens't have this problem :-)

---

### Post by Luxman on 2011-04-10
Great shot!
It fixed my issue as well. Thank you Parama ;)

---

