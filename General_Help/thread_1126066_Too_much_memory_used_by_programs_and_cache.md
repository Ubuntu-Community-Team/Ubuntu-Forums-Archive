---
title: "Too much memory used by programs and cache?"
date: 2009-04-15
forum: General Help
---

### Post by BUKRITYA on 2009-04-15
Hello all.
I am such a newb in these forums, I am still reading welcome messages...
This said, I have been ubuntuing for quite some time now and I just love it!
Having this vast super community to hassle is a true treat. Thanx everyone!

I am running Ibex 64bit on a vaio notebook, with intel's C2D 2.2 GHz and 2GB of RAM, and have recently made 8GB of disk available for swap.
For some reason, I feel as if my memory is being used to the max and this might be slowing down operations like searching for songs on Rhythmbox and even gets my cursor to freeze for several seconds at times. I have included a screenshot with system monitor to try and show this, while running Firefox,Rhythmbox and Document viewer. Visual effects are off since I have disabled my NVidya 8400 to fight heat issues, and I realize top panel is slightly full. Could this be the reason, or is there a workaround?
All hail GNU/Linux-UBUNTU!

---

### Post by fdm on 2009-04-15
is that one instance of firefox with one tab eating 260 megs of ram? what plugins are you using in it? unless evince has an 180mb file open, that is a hell of a mem leak.

---

### Post by Michael.Godawski on 2009-04-15
hi BUKRITYA, 

can you please post the outputs from these terminal commands:

```
top
free -m
```

---

### Post by BUKRITYA on 2009-04-15
Thanx for your reply guys...
@fdm - yup, one instance.

@Michael.Godawski- here is top:

top - 15:53:09 up 1 day,  6:33,  2 users,  load average: 0.21, 0.40, 0.35
Tasks: 147 total,   2 running, 145 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.3%us,  1.9%sy,  0.0%ni, 92.6%id,  0.2%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2047760k total,  2025340k used,    22420k free,   188936k buffers
Swap:  8072324k total,     9276k used,  8063048k free,   765820k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
23300 avi       20   0 1066m 116m  25m S    5  5.8   8:24.68 rhythmbox          
 6263 avi       20   0  217m 5160 3468 S    4  0.3  28:57.38 pulseaudio         
 5955 root      20   0  472m 134m  21m S    4  6.7  36:33.16 Xorg               
22586 avi       20   0  897m 287m  33m S    2 14.4  40:58.38 firefox            
24969 avi       20   0  298m  29m  14m S    2  1.5   0:00.46 gnome-terminal     
 6367 avi       20   0  210m  13m  10m S    1  0.7  12:24.97 multiload-apple    
 6326 avi       20   0  202m 7724 5660 S    0  0.4   1:02.80 gnome-screensav    
    1 root      20   0  4100  852  564 S    0  0.0   0:00.98 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.18 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:05.94 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.14 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:07.54 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:02.18 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:01.96 events/1           

and free -m:
free -m
             total       used       free     shared    buffers     cached
Mem:          1999       1967         31          0        184        736
-/+ buffers/cache:       1046        952
Swap:         7883          9       7874

---

### Post by BUKRITYA on 2009-04-15
It escapes me how to paste these outputs rather than copy paste... No middle click...
 Also I only have GreaseMonkey and Firebug.

---

### Post by kpkeerthi on 2009-04-15
Click on 'Go Advanced' and then click on '#' on the toolbar.

---

### Post by BUKRITYA on 2009-04-15
Gotcha...  THX.```
top - 16:13:06 up 1 day,  6:53,  2 users,  load average: 0.72, 0.43, 0.32
Tasks: 147 total,   1 running, 146 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.0%us,  4.0%sy,  0.0%ni, 84.9%id,  2.1%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2047760k total,  2026612k used,    21148k free,   199820k buffers
Swap:  8072324k total,     9284k used,  8063040k free,   730036k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
22586 avi       20   0  900m 291m  34m S    8 14.6  41:59.28 firefox            
 5955 root      20   0  472m 134m  21m S    7  6.7  37:14.66 Xorg               
23300 avi       20   0 1098m 117m  25m S    5  5.9   9:26.41 rhythmbox          
 6263 avi       20   0  217m 5164 3472 S    4  0.3  29:41.58 pulseaudio         
 6324 avi       20   0  422m  36m  16m S    2  1.8   1:36.13 gnome-panel        
 6314 avi       20   0  184m  16m  10m S    1  0.8   0:58.54 metacity           
 6326 avi       20   0  202m 7724 5660 S    1  0.4   1:04.56 gnome-screensav    
 6367 avi       20   0  210m  13m  10m S    1  0.7  12:33.20 multiload-apple    
 6555 avi       20   0  180m  17m 9.8m S    1  0.9   0:10.28 notification-da    
25135 avi       20   0  298m  29m  14m S    1  1.5   0:00.32 gnome-terminal     
25160 avi       20   0 19100 1340  988 R    1  0.1   0:00.10 top                
 2074 root      15  -5     0    0    0 S    0  0.0   0:37.26 scsi_eh_0          
 6300 avi       20   0  125m 5656 4164 S    0  0.3   2:47.98 at-spi-registry    
 6301 avi       20   0  362m  29m  11m S    0  1.5   0:07.13 gnome-settings-    
    1 root      20   0  4100  852  564 S    0  0.0   0:00.98 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.18 migration/0 
```

```
  total       used       free     shared    buffers     cached
Mem:          1999       1978         21          0        195        713
-/+ buffers/cache:       1070        929
Swap:         7883          9       7874

```

---

### Post by kerry_s on 2009-04-15
unused ram is wasted ram and 8 gig of swap is way to big, next time try 2.5 to 3 giga byte for swap, you want at least the size of your ram for suspend/hibernate.

your memory use looks fine.

---

### Post by fdm on 2009-04-15
is it because there is so much swap that his/her processes are so memory hungry?

---

### Post by kerry_s on 2009-04-15
> **fdm said:**
> is it because there is so much swap that his/her processes are so memory hungry?

i doubt, my guess would be cpu throttling, sounds like it's not cycling up fast enough or not at all.
i would look at> **cat /proc/cpuinfo**
see what it's reading.

---

### Post by BUKRITYA on 2009-04-15
> **kerry_s said:**
> i doubt, my guess would be cpu throttling, sounds like it's not cycling up fast enough or not at all.
i would look at> **cat /proc/cpuinfo**
see what it's reading.
hey kerry_s.
pardon my newbiness, you mean the file located under filesystem/proc/cpuinfo?
The file is there but is completely empty!
anyhoo, my cpu freq monitor shows 800 MHz and when I preform tasks it goes up to 2.20.
The 8GB swap was made by me to try and tend to the memory overload problem.
I have another computer running with 4GB of ram and there I can hardly see the memory monitor, I mean programs and cache take around 20-25% together, so I know there is a 'problem'. can u please explain the CPU issue??
Thanx for all your help.

---

### Post by fdm on 2009-04-15
> **BUKRITYA said:**
> hey kerry_s.
pardon my newbiness, you mean the file located under filesystem/proc/cpuinfo?
The file is there but is completely empty!
anyhoo, my cpu freq monitor shows 800 MHz and when I preform tasks it goes up to 2.20.
The 8GB swap was made by me to try and tend to the memory overload problem.
I have another computer running with 4GB of ram and there I can hardly see the memory monitor, I mean programs and cache take around 20-25% together, so I know there is a 'problem'. can u please explain the CPU issue??
Thanx for all your help.

"cat /proc/cpuinfo" is a command to be used in your terminal. you cant open it in a text editor to view it's contents.

...
there are a couple other posts about large memory usage on this forum but they all seem to be pretty inconclusive. this was a good read, maybe it has something that will help:

[http://www.gentoo-wiki.info/FAQ_Linux_Memory_Management](http://www.gentoo-wiki.info/FAQ_Linux_Memory_Management)

---

### Post by Twitch6000 on 2009-04-15
I think the main issue could be that you are running a 64bit system on a system that only needs to be ran on 32bit.

One thing with 64bit is it does use memory and alot of it.

I know from experience.

However there from this you should also notice speed.

If you would like less memory useage switch to 32bit and the problem should be solved.

Note I said should be solved. If it continues then there could be a hardware problem. Possibly even a software problem.

---

### Post by fdm on 2009-04-15
> **Twitch6000 said:**
> One thing with 64bit is it does use memory and alot of it.

his firefox is eating more then 7 times the memory that mine does under a 32 arch. we both have the same amount of physical memory. that seems pretty far from acceptable. on the systems i have observed, memory consumption on a 64bit OS is a little more then twice then that of a 32bit equivalent. 

switching to a 32bit OS will almost definitely resolve the issue, but at a cost, both in performance and hardware utilization. you bought it so you should be able to observe the benefits.

if all else fails, it might be worthwhile to try out a copy of fedora then debian stable to see if either of those distros suffer from the problem your experiencing.

---

### Post by BUKRITYA on 2009-04-15
Funniest thing....
Now it looks fine, and all I did was shut it off and then turned it on this morning.
Memory consumption seems just fine now, with firefox&rhythmbox running.
Could really be a hardware issue... I get disappointed from the way this vaio works sometimes.
Will do some further research and read the suggested posts.
I realize the 64bit issue, but I'm not one to downgrade for troubleshooting what seems to me something I don't really understand.
My friends always say they are happy with windows XP (yuk), but I tell them "Tempora mutantur, et nos mutamur in illis.&#12521;&#12486;&#12531;&#35486;&#26684;&#22909;&#33391;&#12377;&#12366;&#65346;.The times change and we change with them"
Thanks fo all the insightful suggestions, would love to hear more.

---

