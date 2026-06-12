---
title: "Xorg video performance (and now USB)"
date: 2009-01-08
forum: General Help
---

### Post by akahige on 2009-01-08
I upgraded my bulletproof Hardy system to Intrepid and got bit by the phantom video performance bug(s) where Xorg would eat up >75% of my CPU. (There are a number of them filed in Launchpad, like [this one](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/304262).)

As soon as I could find the time, I was going to reformat the system and go back to Hardy, but the updates of the last couple of days -- which included Xorg and some video drivers -- seem to have cured the issue.

Now I seem to have a problem with the scrollwheel on my USB mouse causing jitters in video playback. (Like if I'm scrolling through a web page and watching something in SMPlayer.) Additionally, I got a boatload of USB related errors on bootup. ("Unable to enumerate usb device on port...")

In looking through dpkg.log, I don't see anything conspicuously USB related (and don't remember seeing anything beyond the first date), so I'm hoping that someone might have some ideas on how I can troubleshoot or solve this...

---

### Post by Arjunanda on 2009-02-15
I'm still having this issue, though I have installed all updates. I noticed I had two problems: first one was firefox specially with gmail, facebook and flash video sites, such as youtube. Installing Firefox 3.1b2 seem to have solved the firefox issue.

Now only this Xorg issue remains. At times it eats up CPU >75%, and remains there for several minutes making the whole system unresponsive. After some time it returns back to normal. Somebody pointed out that ATI cards with compiz are causing trouble. And I have both ATI, and Compiz - though compiz has been disabled for some time, while the problem remains. So I am looking into it now.

Here is how my system looks at times:

```

top - 14:33:34 up  3:57,  3 users,  load average: 1.41, 0.72, 0.53
Tasks: 129 total,   3 running, 126 sleeping,   0 stopped,   0 zombie
Cpu(s): 92.8%us,  6.2%sy,  0.0%ni,  0.0%id,  0.0%wa,  1.0%hi,  0.0%si,  0.0%st
Mem:   1284088k total,  1202864k used,    81224k free,    18440k buffers
Swap:  1590424k total,     5892k used,  1584532k free,   347760k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                     
 5070 root      20   0  436m 145m  13m R 61.4 11.6  44:57.26 Xorg                        
14195 user      20   0  401m 166m  31m S 14.2 13.3   7:01.31 firefox-bin                 
12169 user      20   0  355m 190m  81m R 13.5 15.2   2:49.43 soffice.bin                 
 5637 user      20   0 53416  22m  13m S  2.0  1.8   0:02.46 /usr/lib/glippe             
 5677 user      20   0 98952  62m  12m S  2.0  5.0   3:44.47 skype                       
 5903 user      20   0  134m  57m  21m S  1.6  4.6  14:42.87 exaile                      
 6830 user      20   0 88196  22m  12m S  1.3  1.8   0:32.58 gnome-terminal              
14920 user      20   0  2416 1164  876 R  1.3  0.1   0:10.64 top                         
 4797 chipcard  20   0  4660 1572 1156 S  1.0  0.1   2:08.34 chipcardd4                  
 5509 user      20   0 13960 4836 3608 S  0.7  0.4   3:12.76 at-spi-registry             
 5510 user      20   0 66188  23m  12m S  0.7  1.9   0:53.17 gnome-settings-             
    1 root      20   0  1740  592  512 S  0.0  0.0   0:01.50 init                        
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                    
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                 
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.78 ksoftirqd/0                 
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.02 watchdog/0                  
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.46 events/0     

```

---

