---
title: "the system become slow and the font problem"
date: 2010-03-07
forum: Desktop Environments
---

### Post by apachemaven on 2010-03-07
Hi:
I install Ubuntu after win7,however when I run some application for example eclipse in Ubuntu the system become rather slowly. 
I do know why? This did not occur in my win7 system.
Attach two image about my machine:
[http://imagebin.org/87846](http://imagebin.org/87846)

[http://imagebin.org/87845](http://imagebin.org/87845)


The output of top is :
------------------------------------------------
kingxip@kingxip-c:~$ top

top - 13:38:14 up  1:09,  2 users,  load average: 0.61, 0.65, 0.49
Tasks: 169 total,   1 running, 168 sleeping,   0 stopped,   0 zombie
Cpu(s): 22.5%us,  4.8%sy,  0.0%ni, 72.2%id,  0.3%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   2060592k total,  1506548k used,   554044k free,    59192k buffers
Swap:   979924k total,        0k used,   979924k free,   684084k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
 3427 root      20   0 87416  48m  11m S   36  2.4   6:22.15 Xorg                                                                                            
 6747 kingxip   20   0 50668  13m 9744 S    8  0.7   0:01.08 gnome-terminal                                                                                  
 6221 kingxip   20   0  358m  79m  31m S    5  4.0   2:02.52 firefox-bin                                                                                     
 3696 kingxip   20   0 81600  49m  21m S    3  2.4   1:11.93 compiz.real                                                                                     
 3698 kingxip   20   0  113m  28m  19m S    2  1.4   0:16.28 nautilus                                                                                        
 6619 kingxip   20   0  926m 214m  19m S    1 10.7   0:28.69 java                                                                                            
 6768 kingxip   20   0  2472 1192  884 R    1  0.1   0:00.11 top                                                                                             
   10 root      15  -5     0    0    0 S    0  0.0   0:07.77 events/1                                                                                        
 1336 root      20   0  3420 1144  972 S    0  0.1   0:00.86 hald-addon-stor                                                                                 
 6159 kingxip   20   0 79920  17m  12m S    0  0.9   0:02.99 gedit                                                                                           
    1 root      20   0  2648 1536 1128 S    0  0.1   0:01.00 init                                                                                            
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                        
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                     
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0                                                                                     
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                      
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                     
    7 root      15  -5     0    0    0 S    0  0.0   0:00.38 ksoftirqd/1                                                                                     
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                      
    9 root      15  -5     0    0    0 S    0  0.0   0:00.03 events/0                                                                                        
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 cpuset                                                                                          
   12 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                         
   13 root      15  -5     0    0    0 S    0  0.0   0:00.00 netns                                                                                           
   14 root      15  -5     0    0    0 S    0  0.0   0:00.00 async/mgr                                                                                       
   15 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0                                                                                   
   16 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1                                                                                   
   17 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0                                                                                       
   18 root      15  -5     0    0    0 S    0  0.0   0:00.01 kblockd/1                                                                                       
   19 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                                                          
   20 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                    
   21 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_hotplug                                                                                   
   22 root      15  -5     0    0    0 S    0  0.0   0:00.04 ata/0                                                                                           
   23 root      15  -5     0    0    0 S    0  0.0   0:00.49 ata/1                                                                                           
-----------------------------------------------------------

Is there any problem?

BTW, I am using Ubuntu of English language support, and I like the font of "Lucida Sans Unicode" so I copy it to Ubuntu,and set it to be my default font :
[http://imagebin.org/87847](http://imagebin.org/87847)
It looks well for English character,but rather bad for chinese character when I skin some chinese web site.
In fact I want to use Ubuntu of Chinese support, and I have install this language support, but I have to change it back to English for the undurable ui.

So I wang to know if there is any way to set it display English and Chinese separately and chose the font automatically? for example , use "Lucida Sans Unicode" to display English, other  font which I specified to display Chinese?

---

### Post by apachemaven on 2010-03-07
can anybody do me a favor?

---

