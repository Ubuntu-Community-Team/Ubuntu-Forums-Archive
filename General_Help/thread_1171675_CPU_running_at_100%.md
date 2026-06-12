---
title: "CPU running at 100%"
date: 2009-05-27
forum: General Help
---

### Post by djen9999 on 2009-05-27
I just overcame some other problems with Jaunty only to discover that my CPU is consistently running at or very near 100% all of the time.  I checked processes under system monitor and I can't figure out what most of them are.  In any case, I don't see anything that is hogging my resources.  Nearly everything listed is sleeping, and those applications that are running are in the single digits. (Under %CPU)

I'm not too worried about overheating because I have a heavy duty fan, but this isn't right and I want to fix it if I can.

---

### Post by stefangr1 on 2009-05-27
Can you go to a terminal, type "top" and post the results?

---

### Post by djen9999 on 2009-05-27
Please ignore this, it's incomplete.  See the next post!

dave@dave-desktop:~$ top

top - 17:27:34 up 10:32,  2 users,  load average: 4.29, 4.30, 4.10
Tasks: 146 total,   7 running, 139 sleeping,   0 stopped,   0 zombie
Cpu(s): 71.1%us, 27.6%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  1.3%si,  0.0%st
Mem:    960944k total,   935296k used,    25648k free,    19480k buffers
Swap:  2811332k total,    12376k used,  2798956k free,   449164k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
32223 root      20   0  123m  69m  29m S 11.6  7.4  41:24.28 Xorg               
21091 dave      20   0 32156  20m  14m S  7.6  2.1   3:47.91 gnome-system-mo    
32337 dave      20   0  8224 6432  640 S  4.7  0.7  17:39.76 dbus-daemon        
32277 dave      20   0 26752 7212 5596 R  3.0  0.8  12:36.60 x-session-manag    
32345 dave      20   0  8188 5048 2140 S  3.0  0.5  10:08.27 gconfd-2           
32435 dave      20   0 89652  41m 8252 S  2.0  4.4   6:32.04 compiz.real        
  380 dave      20   0 17536 6388 4692 S  1.3  0.7   3:35.03 gnome-screensav    
19635 dave      20   0  241m  92m  27m R  1.3  9.8   4:30.56 firefox            
32602 dave      20   0 35820  22m 9724 S  1.3  2.4   5:05.59 indicator-apple    
19367 dave      20   0 34176  14m 9972 R  1.0  1.6   0:01.20 gnome-terminal     
32473 dave      20   0 25468 8656 5704 S  1.0  0.9   1:44.11 gnome-power-man    
32480 dave      20   0 91544  24m 3960 S  1.0  2.6   7:24.31 gdl_fs_crawler     
 3291 chipcard  20   0  4756 1240  752 S  0.7  0.1   2:05.31 chipcardd4         
20206 dave      20   0     0    0    0 R  0.7  0.0   0:00.02 vino-server        
32444 dave      20   0 34456  16m 7864 S  0.7  1.7   4:21.32 python             
32459 dave      20   0 88336  26m  14m S  0.7  2.9   1:29.22 pidgin

---

### Post by djen9999 on 2009-05-27
This might be formatted better:

dave@dave-desktop:~$ top

top - 17:32:49 up 10:37,  2 users,  load average: 4.82, 4.50, 4.23
Tasks: 145 total,   3 running, 142 sleeping,   0 stopped,   0 zombie
Cpu(s): 71.9%us, 26.8%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  1.3%si,  0.0%st
Mem:    960944k total,   930164k used,    30780k free,    17284k buffers
Swap:  2811332k total,    12376k used,  2798956k free,   413548k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
32223 root      20   0  141m  89m  47m S 13.9  9.5  42:12.38 Xorg                                                                                            
21091 dave      20   0 32156  20m  14m S  7.0  2.1   4:17.06 gnome-system-mo                                                                                 
19367 dave      20   0 34828  14m 9972 R  5.3  1.6   0:03.52 gnome-terminal                                                                                  
32480 dave      20   0 99368  32m 4000 S  5.3  3.5   7:42.77 gdl_fs_crawler                                                                                  
32337 dave      20   0  8224 6432  640 S  3.0  0.7  17:50.72 dbus-daemon                                                                                     
32277 dave      20   0 26752 7212 5596 S  2.6  0.8  12:44.26 x-session-manag                                                                                 
19635 dave      20   0  241m  92m  27m S  2.3  9.8   4:46.61 firefox                                                                                         
32602 dave      20   0 35948  22m 9724 S  2.0  2.4   5:08.57 indicator-apple                                                                                 
  380 dave      20   0 17536 6388 4692 S  1.7  0.7   3:37.92 gnome-screensav                                                                                 
32345 dave      20   0  8188 5048 2140 S  1.7  0.5  10:14.23 gconfd-2                                                                                        
32372 dave      20   0 30100 9044 6148 S  1.3  0.9   5:16.97 gnome-settings-                                                                                 
24118 dave      20   0 22764 7572 6084 R  1.0  0.8   0:00.03 vino-server                                                                                     
32436 dave      20   0 42276  23m  12m S  1.0  2.6   3:01.81 gnome-panel                                                                                     
32444 dave      20   0 34456  16m 7864 S  1.0  1.7   4:23.88 python                                                                                          
32435 dave      20   0 98.4m  41m 8268 S  0.7  4.4   6:37.12 compiz.real                                                                                     
32473 dave      20   0 25468 8656 5704 S  0.7  0.9   1:45.20 gnome-power-man                                                                                 
 2501 dave      20   0  171m  51m  21m S  0.3  5.5   0:48.97 thunderbird-bin                                                                                 
 3291 chipcard  20   0  4756 1240  752 S  0.3  0.1   2:06.37 chipcardd4                                                                                      
32359 dave      20   0  5616 2104 1768 S  0.3  0.2   0:51.43 gvfsd                                                                                           
32443 dave      20   0 30208  16m  10m S  0.3  1.7   1:00.88 update-notifier                                                                                 
32446 dave      20   0 22884 8856 6480 S  0.3  0.9   1:46.55 gdl_box                                                                                         
32458 dave      20   0 59484  10m 8044 S  0.3  1.1   1:04.77 evolution-alarm                                                                                 
32460 dave      20   0 95392  30m  11m S  0.3  3.3   2:16.89 skype                                                                                           
32469 dave      20   0 24008  11m 7644 S  0.3  1.3   1:10.61 nm-applet                                                                                       
32484 dave      20   0 23312  11m 7948 S  0.3  1.3   0:54.68 notify-osd                                                                                      
32612 dave      20   0 27624  13m 9.8m S  0.3  1.5   1:23.54 fast-user-switc                                                                                 
    1 root      20   0  1908  632  492 S  0.0  0.1   0:01.16 init                                                                                            
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                        
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                     
    4 root      15  -5     0    0    0 S  0.0  0.0   0:02.18 ksoftirqd/0                                                                                     
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                      
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.20 events/0                                                                                        
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                         
    8 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 kstop/0                                                                                         
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                                                                   
   10 root      15  -5     0    0    0 S  0.0  0.0   0:00.27 kblockd/0                                                                                       
   11 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                          
   12 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                    
   13 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue                                                                                          
   14 root      15  -5     0    0    0 S  0.0  0.0   0:02.38 ata/0                                                                                           
   15 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                         
   16 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                                                   
   17 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                           
   18 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                                         
   19 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmmcd                                                                                           
   20 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btaddconn

---

### Post by djen9999 on 2009-05-27
. . . And why so many things running as root?

---

### Post by djen9999 on 2009-05-27
I found it on my own.  It was Vino Server. My next question is why?

---

### Post by sv1cdn on 2009-05-29
> **djen9999 said:**
> I found it on my own.  It was Vino Server. My next question is why?

I also asked a similar question to launchpad.net

> Hello world!
Running Ubuntu jaunty 9.04 up to date. Had the same problem in three different installations!
I have activated remote desktop so the vino-server process is running. Had no problems until I decided to check in Startup Applications the Automatically remember running applications when logging out.
After restart I log in, and have extreme CPU usage in one core. vino-server process is starting up and terminating again and again! Only top from command line made me see this. When I sudo killall vino-server cpu returns to normal levels.
Any idea? Bug?

But more than a week now, never got a reply! Just posted the same question in Ubuntu forum - General Help. The weird about me was that the vino-server process acted so wild and only top from shell showed this.

---

### Post by djen9999 on 2009-06-02
I really wanted to be able to use my remote desktop but seeing that line top out at 100% and stay there was scary.

Top was what exposed the problem to me too.  I'm glad I was able to find the culprit.  Please share if you get an answer from Launchpad.

---

### Post by sv1cdn on 2009-06-04
Here is the reply from launchpad:

> Yes, this has been reported several times but there is not a good
solution yet.  Check this bug report for more details:
[https://bugs.launchpad.net/vino/+bug/340515](https://bugs.launchpad.net/vino/+bug/340515)

---

