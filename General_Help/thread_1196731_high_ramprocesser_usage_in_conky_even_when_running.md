---
title: "high ram/processer usage in conky even when running no apps"
date: 2009-06-25
forum: General Help
---

### Post by kmaster228 on 2009-06-25
hi all recently conky has been displaying very high ram usage and processer usage, one of my processors is permanently on 100% is this normal when only running firefox and emesene? or am i just worrried for no reason
i have a quad core computer
[ATTACH]118918[/ATTACH]
[ATTACH]118919[/ATTACH]

---

### Post by credobyte on 2009-06-25
I wouldn't worry about RAM - 23% isn't that much ;) About CPU - can you post the output of _top_ command ?

---

### Post by philcamlin on 2009-06-25
23% ram thats not bad at all :popcorn:

---

### Post by kmaster228 on 2009-06-25
kushal@kushal-desktop:~$ top

top - 00:10:33 up  4:37,  2 users,  load average: 1.40, 1.38, 1.31
Tasks: 205 total,   3 running, 201 sleeping,   0 stopped,   1 zombie
Cpu(s): 12.9%us, 18.5%sy,  0.0%ni, 68.5%id,  0.0%wa,  0.1%hi,  0.1%si,  0.0%st
Mem:   3350656k total,  3070540k used,   280116k free,   238344k buffers
Swap:   706820k total,        0k used,   706820k free,  1765004k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3655 root      20   0 69904 2808 1108 S  100  0.1 277:55.24 nakido             
 4659 kushal    20   0  577m 231m  32m S   11  7.1  18:50.52 firefox            
 3357 root      20   0  180m  69m  23m S    7  2.1  13:03.07 Xorg               
 6345 kushal    20   0  105m  59m  15m S    3  1.8   3:06.19 compiz.real        
 4131 kushal    20   0 49876  16m 9.9m S    2  0.5   2:56.05 awn                
 3899 kushal    20   0  228m 5928 4528 S    1  0.2   3:09.99 pulseaudio         
 4524 kushal    20   0 13116 3604 2248 S    1  0.1   4:03.08 conky              
 4027 kushal    20   0 39800  20m  10m S    1  0.6   1:17.24 python             
 4033 kushal    20   0  110m  37m  15m S    1  1.1   1:12.50 python             
 6118 kushal    20   0  564m 200m  29m S    1  6.1   1:33.53 java               
22097 kushal    20   0 36060  14m 9920 S    1  0.4   0:00.47 gnome-terminal     
   13 root      15  -5     0    0    0 S    0  0.0   0:00.86 ksoftirqd/3        
   36 root      15  -5     0    0    0 S    0  0.0   0:00.14 ata/1              
 4006 kushal    20   0 39088  20m  11m S    0  0.6   1:11.22 python             
 4045 kushal    20   0 66268  29m  18m S    0  0.9   0:01.18 beagle-search      
 4088 kushal    20   0  676m 128m  56m S    0  3.9   1:13.95 amarok             
 4178 kushal    20   0 22508 9472 7856 S    0  0.3   0:14.99 geyes_app


i dont mean the system monitor one i mean the one in conky the one that says memory

---

### Post by credobyte on 2009-06-25
1) Use [code] tags ( sorry, I'm not going to count columns and rows )
2) conky can show anything .. that's why I asked you to show the _top_.

---

### Post by kmaster228 on 2009-06-25
sorry about that ill use the code tags :s

```

top - 01:14:11 up  5:40,  2 users,  load average: 2.01, 1.94, 1.91
Tasks: 205 total,   3 running, 201 sleeping,   0 stopped,   1 zombie
Cpu(s): 16.8%us, 24.2%sy,  0.0%ni, 59.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3350656k total,  3170692k used,   179964k free,   203948k buffers
Swap:   706820k total,        0k used,   706820k free,  1776396k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3655 root      20   0 44740 3820 1120 R   97  0.1 340:21.14 nakido             
 4659 kushal    20   0  789m 346m  35m S   37 10.6  41:17.14 firefox            
 3357 root      20   0  176m  73m  26m R   18  2.2  18:24.03 Xorg               
 4131 kushal    20   0 50256  17m 9.9m S    3  0.5   3:26.78 awn                
 6345 kushal    20   0  108m  61m  15m S    3  1.9   4:18.20 compiz.real        
22789 kushal    20   0 36444  14m 9.8m S    2  0.4   0:00.86 gnome-terminal     
 3899 kushal    20   0  228m 5940 4528 S    1  0.2   3:55.35 pulseaudio         
 4033 kushal    20   0  110m  37m  15m S    1  1.1   1:37.70 python             
 4524 kushal    20   0 13116 3604 2248 S    1  0.1   5:00.24 conky              
 4006 kushal    20   0 39088  20m  11m S    1  0.6   1:27.09 python             
 1606 kushal    20   0  2580 1240  912 R    0  0.0   0:00.06 top                
 3902 kushal    20   0  7652 4572 2188 S    0  0.1   0:06.32 gconfd-2           
 3933 kushal    20   0 30928  10m 6856 S    0  0.3   0:02.62 gnome-settings-    
 3995 kushal    20   0 66976  29m  15m S    0  0.9   0:05.38 gnome-panel        
 4008 kushal    20   0 39768  20m  11m S    0  0.6   0:39.13 python             
 4025 kushal    20   0 65488  33m  16m S    0  1.0   0:09.30 gnome-do           
 4027 kushal    20   0 39800  20m  10m S    0  0.6   1:46.61 python             

```

what do you mean conky can show anythings? isnt what conky shows is my ram usage?

---

### Post by Chemical Imbalance on 2009-06-25
Whatever "nakido" is, it is the culprit.

It is running as root, too btw.

---

### Post by credobyte on 2009-06-25
Conky is an application and we all know, applications love to say "sorry" ! Anyway, what's "nakido" ?

---

### Post by kmaster228 on 2009-06-25
nakido is supposed to be a client for a online storage site called nakido except it doesnt work and i cant start the client...i thought i removed nakido sudo apt-get remove nakdio and it said it removed the app?! and its running on root...thats not very good for something online. anyway how do i make conky correct?

---

### Post by Celauran on 2009-06-25
> **kmaster228 said:**
> nakido is supposed to be a client for a online storage site called nakido except it doesnt work and i cant start the client...i thought i removed nakido sudo apt-get remove nakdio and it said it removed the app?! and its running on root...thats not very good for something online. anyway how do i make conky correct?

It doesn't look like there *is* anything to correct in conky. You can see in top that this nakido thing is still running and eating up 97% CPU. I'd start by killing that process.

---

### Post by credobyte on 2009-06-25
Open System-Administration-Services, remove this "nakido" & restart your PC.

---

### Post by kmaster228 on 2009-06-25
i killed and removed the app yesterday i wonder how its back

---

