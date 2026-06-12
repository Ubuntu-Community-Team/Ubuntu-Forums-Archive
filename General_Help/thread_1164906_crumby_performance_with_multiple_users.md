---
title: "crumby performance with multiple users"
date: 2009-05-20
forum: General Help
---

### Post by scarf on 2009-05-20
hi i have a computer which used to have windows xp pro on it, and i finally installed ubuntu 9.04 on it when the anti-virus expired.  the performance is really crumby when 2 users are logged on.

the system has an AMD athlon 64 3200+ and 512 MB of i think DDR2 400 MHz memory, 2 SATA hard drives in RAID-1 configuration.

when windows was installed there was actually 4 user accounts, and all of them could be logged on at once and there really wasn't much of a slowdown.

now, with ubuntu 9.04 amd64 installed, i have only added 2 users.  the system seems to work pretty fine when just one user is on.  but, as soon as i try to switch user and log on the second user, it brings the system to it's knees.

after logging on the second user, the system monitor shows that all of the RAM is in use (dark green) and about 750 MB of the swap space becomes used, whereas, when one user is logged on only about 1/2 of the RAM is in use and none of the swap is used.

the only thing i can think of that might cause this is that i setup the system with an encrypted drive using the alternate install disc, whereas i didn't have such a setup when windows was installed.  can that make this big of a difference?

so, understand that the users are simply logged in, and there's no extra apps running.

it took at least 15 minutes to install 5 updates, when that usually only takes like 15 seconds when just one user is logged on.

this horrible performance is really annoying, as it's a family computer and multiple users become logged on.  nothing is really used besides firefox.

can you please help me to get this computer to perform as well as it used to?  thanks.

---

### Post by mb_webguy on 2009-05-20
Linux was designed from the beginning as a multi-user system ("multi" meaning thousands in the case of some servers), whereas Windows was initially designed as a single-user system, and the ability to have multiple was tacked on later.  So your problem seems especially strange.  

512MB isn't a lot of memory, and you might want to consider upgrading, but that wouldn't explain the poor performance relative to Windows.  Linux and the Gnome desktop tend to use considerably fewer resources than Windows, so if Windows ran fine with multiple users, Ubuntu should run much better.

Try this...  Login to both of the user accounts, and in one open the terminal and enter the command "top".  This will show you a detailed listing of your system resources and running processes.  You can sort by different columns using "<" (Shift+,) and ">" (Shift+.).  If you're getting poor performance, check the entries for Cpu and Mem at the top to see if usage for either is unusually high, and sort the running processes by the %CPU (the default) and %MEM (by pressing ">") to see which ones are using up resources.  If you can't figure out from that where the problem lies, copy and paste the output of top here so we can help you work it out.

---

### Post by scarf on 2009-05-27
> **mb_webguy said:**
> 
Try this...  Login to both of the user accounts, and in one open the terminal and enter the command "top".  This will show you a detailed listing of your system resources and running processes.  You can sort by different columns using "<" (Shift+,) and ">" (Shift+.).  If you're getting poor performance, check the entries for Cpu and Mem at the top to see if usage for either is unusually high, and sort the running processes by the %CPU (the default) and %MEM (by pressing ">") to see which ones are using up resources.  If you can't figure out from that where the problem lies, copy and paste the output of top here so we can help you work it out.

hi, thanks for your suggestion. sorry for the late reply; i don't have instant access to the console of the system.

i logged into the second account and ran firefox, something that i did all the time when windows was installed.  it seems firefox is using a lot of the memory.  output of top, sorted by %MEM:

```

top - 17:44:18 up 6 days, 22:25,  4 users,  load average: 2.59, 1.25, 0.48
Tasks: 161 total,   4 running, 155 sleeping,   0 stopped,   2 zombie
Cpu(s):  4.6%us,  2.3%sy,  0.0%ni, 93.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    483812k total,   475580k used,     8232k free,     5116k buffers
Swap:  1417208k total,   162868k used,  1254340k free,    82936k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
29695 patty     20   0  561m 105m  12m S  0.7 22.4   0:27.83 firefox            
31154 scar      20   0  469m  55m  22m S  2.0 11.8   0:03.24 firefox            
31059 scar      20   0  313m  19m  11m S  0.0  4.1   0:01.98 gnome-panel        
29683 patty     20   0  310m  18m 7616 S  0.0  3.8   0:01.78 checkgmail         
30259 root      20   0  104m  16m 5140 R  1.7  3.6   0:04.15 Xorg               
31066 scar      20   0  211m  16m 7368 S  0.0  3.6   0:00.39 python             
31128 scar      20   0  196m  15m 8584 R  0.7  3.3   0:01.65 gnome-terminal     
31077 scar      20   0  232m  15m 9744 S  0.0  3.3   0:00.42 update-notifier    
31104 scar      20   0  262m  15m 8064 S  0.0  3.2   0:00.51 mixer_applet2      
31060 scar      20   0  348m  13m 8076 S  0.0  2.9   0:00.94 nautilus           
26457 patty     20   0  315m  13m 8868 S  0.0  2.8   0:01.94 gnome-panel        
25993 root      20   0  103m  12m 4448 S  0.0  2.7   0:08.61 Xorg               
26028 patty     20   0  197m  12m 7360 S  0.0  2.6   0:00.53 x-session-manag    
31058 scar      20   0  159m  11m 8388 S  0.0  2.5   0:00.80 metacity           
31090 scar      20   0  210m  10m 6092 S  0.0  2.1   0:00.33 trashapplet        
26510 patty     20   0  240m 9532 7164 S  0.0  2.0   0:00.25 gweather-applet    
31107 scar      20   0  208m 8732 6232 S  0.0  1.8   0:00.15 indicator-apple    
31051 scar      20   0  220m 8708 5264 S  0.0  1.8   0:00.28 gnome-settings-    
26456 patty     20   0  158m 8552 7244 S  0.0  1.8   0:01.55 metacity           
31080 scar      20   0  221m 8228 4504 S  0.0  1.7   0:00.10 gnome-power-man    
31101 scar      20   0  205m 7916 5832 S  0.0  1.6   0:00.16 multiload-apple    
31087 scar      20   0  143m 7748 5600 S  0.0  1.6   0:00.07 notify-osd         
26503 patty     20   0  216m 7532 6752 S  0.0  1.6   0:01.76 multiload-apple    
26469 patty     20   0  231m 7476 6900 S  0.0  1.5   0:00.41 update-notifier    
26458 patty     20   0  344m 7268 6456 S  0.0  1.5   0:00.71 nautilus           
26506 patty     20   0  270m 7196 6692 S  0.0  1.5   0:00.26 mixer_applet2      
30463 scar      20   0  169m 6680 4880 S  0.0  1.4   0:00.23 x-session-manag    
26477 patty     20   0  187m 6592 5892 S  0.0  1.4   0:00.34 nm-applet          
26513 patty     20   0  208m 6136 5408 S  0.0  1.3   0:00.13 indicator-apple    
29732 patty     20   0 60996 6048 1116 R  1.7  1.3   0:04.86 npviewer.bin       
31034 scar      20   0  161m 6048 3912 S  0.0  1.3   0:00.11 seahorse-agent     
26481 patty     20   0  210m 5872 5532 S  0.0  1.2   0:00.17 trashapplet        
26446 patty     20   0  220m 5596 4860 S  0.0  1.2   0:00.45 gnome-settings-    
26499 patty     20   0  143m 5440 5336 S  0.0  1.1   0:00.04 notify-osd         
26464 patty     20   0  211m 5428 4844 S  0.0  1.1   0:00.34 python             
31021 scar      20   0 45756 5080 2104 S  0.0  1.0   0:00.34 gconfd-2           
26497 patty     20   0  221m 4672 4112 S  0.0  1.0   0:00.12 gnome-power-man    
26537 patty     20   0  158m 4660 3804 S  0.0  1.0   0:00.58 gnome-screensav    
31018 scar      20   0  315m 4128 2400 S  0.0  0.9   0:00.67 pulseaudio         
26302 patty     20   0  161m 3796 3792 S  0.0  0.8   0:00.05 seahorse-agent     
31168 scar      20   0 20972 3664 1448 S  0.0  0.8   0:00.21 bash               
31130 scar      20   0 20972 3640 1408 S  0.0  0.8   0:00.21 bash               
31096 scar      20   0 56136 3284 2264 S  0.0  0.7   0:00.05 gvfs-hal-volume    
31062 scar      20   0 86868 3164 2184 S  0.0  0.7   0:00.16 bonobo-activati    
 2940 root      20   0 37512 3036 1008 S  0.0  0.6   0:19.66 ddclient           
26175 patty     20   0 45780 2984 2036 S  0.0  0.6   0:00.54 gconfd-2           
31098 scar      20   0 54488 2960 1936 S  0.0  0.6   0:00.02 gvfs-gphoto2-vo    
31150 scar      20   0  158m 2728 1348 S  0.0  0.6   0:00.24 gnome-screensav    
30256 root      20   0  140m 2568 1800 S  0.0  0.5   0:00.04 gdm                
30452 scar      20   0 75900 2404 1820 S  0.0  0.5   0:00.03 gnome-keyring-d    
31094 scar      20   0 45160 2396 1904 S  0.0  0.5   0:00.02 gvfsd-trash        
31019 scar      20   0 68048 2344 1816 S  0.0  0.5   0:00.00 gconf-helper  

```

i then started the update manager and checked for updates.  the %MEM of both firefox processes went down, but the other user's (patty) firefox process still took up a large amount of memory.  the swap file almost doubled.  the machine was still acting very sluggish.  here's the output of top after i ran update manager (this one is still sorted by %CPU, sorry):

```

top - 17:46:30 up 6 days, 22:27,  4 users,  load average: 4.03, 2.05, 0.85
Tasks: 161 total,   3 running, 156 sleeping,   0 stopped,   2 zombie
Cpu(s): 19.9%us, 11.3%sy,  0.0%ni,  0.0%id, 67.8%wa,  0.7%hi,  0.3%si,  0.0%st
Mem:    483812k total,   381984k used,   101828k free,     3988k buffers
Swap:  1417208k total,   318300k used,  1098908k free,    75452k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
29695 patty     20   0  561m  77m  10m D  7.3 16.3   0:30.46 firefox            
  923 root      15  -5     0    0    0 S  6.0  0.0   2:43.09 kcryptd            
30259 root      20   0  106m  12m 3704 S  3.7  2.6   0:08.01 Xorg               
29732 patty     20   0 60996 2596 1080 R  3.0  0.5   0:07.34 npviewer.bin       
31059 scar      20   0  318m  11m 6396 S  1.3  2.5   0:03.03 gnome-panel        
31058 scar      20   0  159m 7416 5524 S  0.7  1.5   0:01.07 metacity           
31154 scar      20   0  470m  31m 8784 S  0.7  6.7   0:03.63 firefox            
31196 scar      20   0 19116  864  520 R  0.7  0.2   0:00.43 top                
  922 root      15  -5     0    0    0 S  0.3  0.0   0:06.70 kcryptd_io         
25993 root      20   0  103m 7044 1924 D  0.3  1.5   0:08.72 Xorg               
31066 scar      20   0  211m 4268 2960 S  0.3  0.9   0:00.40 python             
31128 scar      20   0  196m 6840 4688 S  0.3  1.4   0:02.29 gnome-terminal     
31150 scar      20   0  158m 1332  972 S  0.3  0.3   0:00.40 gnome-screensav    
    1 root      20   0  5244  228  148 S  0.0  0.0   0:01.38 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.87 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.32 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    8 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 kstop/0            
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0      
   10 root      15  -5     0    0    0 R  0.0  0.0   0:00.22 kblockd/0          
   11 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   12 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
   13 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue             
   14 root      15  -5     0    0    0 S  0.0  0.0   1:34.82 ata/0              
   15 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux            
   16 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd      
   17 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd              
   18 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
   19 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmmcd              
   20 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btaddconn          
   21 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btdelconn          
   24 root      15  -5     0    0    0 S  0.0  0.0   0:07.92 kswapd0            
   25 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0              
   26 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ecryptfs-kthrea    
   29 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0          
   30 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1          
   31 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2          
   32 root      15  -5     0    0    0 S  0.0  0.0   2:14.85 scsi_eh_3          
   33 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kstriped           
   34 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmpathd/0          
   35 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmpath_handlerd    
   36 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksnapd             
   37 root      15  -5     0    0    0 S  0.0  0.0   0:02.47 kondemand/0        
   38 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd           
  437 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt           
  458 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0        
  809 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kdmflush           
  813 root      15  -5     0    0    0 S  0.0  0.0   0:24.26 kmirrord           
  814 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kcopyd  

```

---

### Post by scarf on 2009-06-02
hello, i think the problem was with checkgmail, maybe.  even tho it wasn't using much memory when i posted the above top logs, after about 5 more days it was using more than 50% of the memory.  i filed [a bug report](https://bugs.launchpad.net/ubuntu/+source/checkgmail/+bug/382267) about it.

now that i have killed checkgmail, i am able to log into both accounts and the system is running much smoother.  using igoogle.com instead.

---

### Post by steveneddy on 2009-06-02
But he isn't actually allowing four different people to log onto the computer it seems. It looks like he wrote that he created multiple users and only logs off of one user profile (or maybe suspends it temporarily) to log himself into another user profile.

Is this true or am I mistaken?

EDIT:

Maybe the user would consider using the server version of Ubuntu if he hasn't already. My Hardy install on a server with a PIII processor and only 512 mb RAM will handle six users simultaneously in the house with no performance degradation on any of the six machines. They all log in remotely and use most of the server's resources as their own. I even log in remotely to this server while on the road and no one at the house can tell that I am even on the network.

---

### Post by scarf on 2009-06-03
what is happening is one user logs on and then we choose "switch user" and log on another user, etc.

i did not know it was possible to have multiple x sessions going.

what do you mean six users simultaneously?  how do they log in?  how do you log in remotely?  an ssh session doesn't use much resources, but when using a full x session or even just a firefox process that is where resources become tight....

---

### Post by dcstar on 2009-06-03
> **scarf said:**
> 
..........
the only thing i can think of that might cause this is that i setup the system with an encrypted drive using the alternate install disc, whereas i didn't have such a setup when windows was installed.  can that make this big of a difference?
.........

Yes, encryption is a CPU intensive function and if you have multiple processes running - all potentially doing disk i/o even when not actually in use - it is an additional burden on a system with such a small amount of RAM.

The simple solution is to spend a few dollars and give your hardware sufficient resources.

---

