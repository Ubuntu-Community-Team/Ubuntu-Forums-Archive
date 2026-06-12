---
title: "after jaunty upgrade now system is very slow"
date: 2009-06-16
forum: General Help
---

### Post by ubuntumaybe on 2009-06-16
Hi,

Since I have upgraded to jaunty my system has been operating very slow. It seems to boot quicker but after I have workig on the system for a short time the hard drive light stays on for a long time after every mouse click or key entry and then the system freezes. It is very annoying. I never had this problem with earlier releases.
I have a compaq r3000 with 512 meg ram, 80 gig harddrve. Thanks for your help.

---

### Post by DeMus on 2009-06-16
> **ubuntumaybe said:**
> Hi,

Since I have upgraded to jaunty my system has been operating very slow. It seems to boot quicker but after I have workig on the system for a short time the hard drive light stays on for a long time after every mouse click or key entry and then the system freezes. It is very annoying. I never had this problem with earlier releases.
I have a compaq r3000 with 512 meg ram, 80 gig harddrve. Thanks for your help.

Please open a terminal and type
```
top
```

Copy paste the output of the screen here so we can see which program is using up all your CPU.

---

### Post by Therion on 2009-06-16
> **ubuntumaybe said:**
> Since I have upgraded to jaunty my system has been operating very slow. 

I'm going to guess, just a *guess* now, that you did an online upgrade instead of a clean install?

---

### Post by ubuntumaybe on 2009-06-16
> **Therion said:**
> I'm going to guess, just a *guess* now, that you did an online upgrade instead of a clean install?

Hi,

Good guess. I had the previous release and over a period of time I upgraded via the upgrade manager. Hope this helps.

---

### Post by Therion on 2009-06-16
> **ubuntumaybe said:**
> Good guess. 
It was easier than you might think.

> **ubuntumaybe said:**
> I had the previous release and over a period of time I upgraded via the upgrade manager. Hope this helps.
Could you explain in more detail what you mean by "*over a period of time* I upgraded..." for me, please?

---

### Post by blackhawks_fan on 2009-06-16
> **ubuntumaybe said:**
> Hi,

Since I have upgraded to jaunty my system has been operating very slow. It seems to boot quicker but after I have workig on the system for a short time the hard drive light stays on for a long time after every mouse click or key entry and then the system freezes. It is very annoying. I never had this problem with earlier releases.
I have a compaq r3000 with 512 meg ram, 80 gig harddrve. Thanks for your help.
I did the online upgrade and had several minor problems (sound, video, flash, the new notification system didn't work, OS sluggish and unresponsive at times...)  Wasn't happy at all.  Did a full install from CD and now I am very happy that I upgraded.  Clean install seems to be the way to go.

---

### Post by TrakerJon on 2009-06-16
I agree...upgrading seems to be problematic at best. Doing a clean install will most likely give you the desired results.

This post should help you install things fairly quickly once you've got the OS up and running...**[http://ubuntuforums.org/showthread.php?t=1181327](http://ubuntuforums.org/showthread.php?t=1181327)**

---

### Post by Therion on 2009-06-16
> **blackhawks_fan said:**
> Clean install seems to be the way to go.
From what I've read, and experienced, over the years with Ubuntu doing an online upgrade will, *most likely*, go off without a hitch.  However, doing a clean install seems to almost guarantee a good overall Ubuntu-Experience. There are no real guarantees in life but the clean install is is about as close as you can get.  Online upgrades are just flaky. No two ways about it.  After doing your clean install, download, install and run **QuickStart**.  

QuickStart will get your codecs, flash, java and commonly requested applications installed and running with just a few keystrokes.

[http://quickstart.phpbb.net/viewtopic.php?f=8&t=11](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11)

---

### Post by ManiacDan on 2009-06-16
Before you go formatting and re-installing, check the system monitor for enormous CPU usage from indicator-applet.  If it's using more than 2-3% CPU, or if it uses CPU for more than 2 seconds at a time, try to install the [indicator-messages - 0.1.6-0ubuntu2~ppa2]("https://launchpad.net/~ted/+archive/bugfix") patch.  It seems like a problem common enough to be known about, but not common enough to be widely patched, which is the worst kind of problem.  

-Dan

---

### Post by ubuntumaybe on 2009-06-16
Hi,

I do not know where to begin to respond to all of your responses. I will begin by saying that I am uncomfortable about doing a re-install of the os. I installed many apps over a period of time and I do not want to go through the process of re-installing them. If there is a way of doing an upgrade then I would be interested. Ubuntu is now my main os. Over a period of time would mean weeks. I get my internet connection from a library and with so much to download I could not stay in the library that long. I shall install that patch when I get the chance. I am currently on a wired ethernet computer at the library. The problem with running the top command or getting info on processor usage is that the laptop freezes and it will not accept mouse clicks or keyboard entry. I then have to press the power on button to exit the system. Thanks for your help in this matter.

---

### Post by ManiacDan on 2009-06-16
If your machine freezes while running top you need a re-install anyway.  Good luck though.

-Dan

---

### Post by ubuntumaybe on 2009-06-17
> **ManiacDan said:**
> If your machine freezes while running top you need a re-install anyway.  Good luck though.

-Dan

Hi,

I may not have made myself clear. What I meant was that the laptop freezes and I cannot open a treminal window to execute the top command. I ran top before the laptop froze and I see that a program called tor is running with the user debian-t. I did not start that program. I checked the services and I do not see it listed. I also stopped all mysql and apache services. I am on a wired ethernet connection at my library. Thanks for your help in this matter.

---

### Post by ubuntumaybe on 2009-06-19
> **DeMus said:**
> Please open a terminal and type
```
top
```

Copy paste the output of the screen here so we can see which program is using up all your CPU.

Hi,

I have not forgotten you. I cannot run the top command because when the laptop freezes I cannot open a terminal window to execute the command. I am not too familiar with linux. I need to be able to run the top command in the background and have it execute every 30sec and write the results to a file. How cann that be done. Thanks.

---

### Post by ubuntumaybe on 2009-06-20
Hi,

I ran top in the background and piped it to a file. This is the output. Hope it is helpful. This problem is very annoying. THanks


top - 13:36:45 up 20 min,  4 users,  load average: 22.21, 9.81, 4.14
Tasks: 156 total,   3 running, 153 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  4.9%sy,  0.0%ni,  6.3%id, 88.4%wa,  0.3%hi,  0.2%si,  0.0%st
Mem:    482556k total,   477552k used,     5004k free,      160k buffers
Swap:        0k total,        0k used,        0k free,    52376k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
  156 root      15  -5     0    0    0 D  0.8  0.0   0:02.00 kswapd0            
 6641 jkerr     20   0  155m  78m 1028 D  0.6 16.7   0:49.58 opera              
 2116 root      15  -5     0    0    0 D  0.5  0.0   0:00.52 kjournald          
 5561 haldaemo  20   0  6848 1728  928 D  0.5  0.4   0:00.66 hald               
 5674 root      20   0 76832  21m  992 D  0.5  4.6   0:58.25 Xorg               
 6305 jkerr     20   0  9416 1384  620 D  0.5  0.3   0:00.10 gvfs-gphoto2-vo    
 6531 root      20   0  2276  796  668 S  0.5  0.2   0:00.08 dhclient           
 7748 mail      20   0  3164  784  604 D  0.5  0.2   0:00.10 smtp               
 5421 debian-t  20   0 12904 6836  656 D  0.3  1.4   0:04.96 tor                
 5690 root      20   0 16548 1224  684 D  0.3  0.3   0:00.42 NetworkManager     
 6147 jkerr     20   0  9020 3456  796 D  0.3  0.7   0:00.66 gconfd-2           
 6182 jkerr     20   0 38072 4636  900 D  0.3  1.0   0:03.76 metacity           
 6303 jkerr     20   0 25440 1636  884 D  0.2  0.3   0:00.13 gvfs-hal-volume    
 3233 root      15  -5     0    0    0 S  0.2  0.0   0:03.92 ntos_wq            
 5324 nobody    20   0  2388  536  404 S  0.2  0.1   0:00.04 dnsmasq            
 5523 ntp       20   0  4340  948  648 D  0.2  0.2   0:00.08 ntpd               
 5541 root      20   0  2116  536  432 D  0.2  0.1   0:00.06 dhcdbd             
 5636 root      20   0  5180  640  424 D  0.2  0.1   0:00.30 hald-addon-stor    
 5698 root      20   0  7068 1220  676 D  0.2  0.3   0:00.18 nm-system-setti    
 6057 jkerr     20   0 26740 1272  676 D  0.2  0.3   0:00.12 gnome-keyring-d    
 6144 jkerr     20   0 95732 2676 1320 D  0.2  0.6   0:00.26 pulseaudio         
 6185 jkerr     20   0  110m  13m 1128 D  0.2  2.9   0:09.68 nautilus           
 6191 jkerr     20   0 44516 4948 1012 D  0.2  1.0   0:00.70 update-notifier    
 6244 jkerr     20   0  7012 1316  856 D  0.2  0.3   0:00.14 gvfsd-trash        
 7242 jkerr     20   0 11560 2508  784 D  0.2  0.5   0:01.06 manedit            
 7711 jkerr     20   0 17016 9.9m  840 D  0.2  2.1   0:00.56 python             
 7747 root      20   0  4820  308  168 D  0.2  0.1   0:00.06 hal-storage-unm    
 7749 root      20   0  4600  224  116 D  0.2  0.0   0:00.08 hal-storage-unm    
 6936 jkerr     39  19 62448  11m  988 R  0.1  2.4   0:52.21 operapluginwrap    
    1 root      20   0  3084 1332    8 S  0.0  0.3   0:01.22 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.08 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   41 root      15  -5     0    0    0 R  0.0  0.0   0:00.36 kblockd/0          
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  120 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  154 root      20   0     0    0    0 D  0.0  0.0   0:00.06 pdflush            
  155 root      20   0     0    0    0 D  0.0  0.0   0:00.10 pdflush            
  197 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0              
 1070 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksnapd             
 1196 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd      
 1200 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd              
 1216 root      15  -5     0    0    0 S  0.0  0.0   0:00.08 ata/0              
 1221 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux            
 1224 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt           
 1806 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0          
 1808 root      15  -5     0    0    0 S  0.0  0.0   0:00.16 scsi_eh_1          
 1958 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0        
 2267 root      16  -4  2392  328    8 S  0.0  0.1   0:00.38 udevd              
 3230 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 pccardd            
 3235 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ndis_wq            
 3237 root      15  -5     0    0    0 S  0.0  0.0   0:00.18 wrapndis_wq        
 3265 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused          
 3294 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 pccardd            
 3483 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 tifm               
 3488 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmmcd              
 3956 daemon    20   0  1940  108    8 S  0.0  0.0   0:00.00 portmap            
 3976 statd     20   0  2004  120    8 S  0.0  0.0   0:00.00 rpc.statd          
 4058 root      20   0  1808   76    8 S  0.0  0.0   0:00.00 getty              
 4059 root      20   0  1808   76    8 S  0.0  0.0   0:00.00 getty              
 4066 root      20   0  1808   80    8 S  0.0  0.0   0:00.00 getty              
 4069 root      20   0  1808   76    8 S  0.0  0.0   0:00.00 getty              
 4071 root      20   0  1808   76    8 S  0.0  0.0   0:00.00 getty              
 4095 root      20   0  2200  552    8 S  0.0  0.1   0:00.00 acpid              
 4140 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kondemand/0        
 4215 syslog    20   0  2040  140    8 D  0.0  0.0   0:00.30 syslogd            
 4236 root      20   0  1968  104    8 S  0.0  0.0   0:00.04 dd                 
 4238 klog      20   0  3396 1764    8 S  0.0  0.4   0:00.14 klogd              
 4259 messageb  20   0  3008  576    8 S  0.0  0.1   0:00.56 dbus-daemon        
 4278 Slmodemd  RT   0  4176 4172 3740 S  0.0  0.9   0:00.02 slmodemd           
 4523 root      20   0 16356 1500  704 S  0.0  0.3   0:00.06 console-kit-dae    
 4595 clamav    20   0 81452  68m  388 S  0.0 14.5   0:00.00 clamd              
 4711 clamav    20   0  3228  844  616 S  0.0  0.2   0:00.00 freshclam          
 5101 root      20   0  1944  572  356 S  0.0  0.1   0:00.00 hddtemp            
 5148 root      20   0 52464 1444  796 S  0.0  0.3   0:00.04 libvirtd           
 5162 root      20   0  2956  712  468 S  0.0  0.1   0:00.00 lshd               
 5201 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 rpciod/0           
 5248 root      20   0     0    0    0 S  0.0  0.0   0:00.00 lockd              
 5249 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 nfsd4              
 5250 root      20   0     0    0    0 S  0.0  0.0   0:00.00 nfsd               
 5251 root      20   0     0    0    0 S  0.0  0.0   0:00.00 nfsd               
 5252 root      20   0     0    0    0 S  0.0  0.0   0:00.00 nfsd               
 5253 root      20   0     0    0    0 S  0.0  0.0   0:00.00 nfsd               
 5254 root      20   0     0    0    0 S  0.0  0.0   0:00.00 nfsd               
 5255 root      20   0     0    0    0 S  0.0  0.0   0:00.00 nfsd               
 5256 root      20   0     0    0    0 S  0.0  0.0   0:00.00 nfsd               
 5257 root      20   0     0    0    0 S  0.0  0.0   0:00.00 nfsd               
 5281 root      20   0  2120  284  140 S  0.0  0.1   0:00.00 rpc.mountd         
 5325 mail      20   0  2980  512  376 S  0.0  0.1   0:00.12 nullmailer-send    
 5374 privoxy   20   0  2764  784  364 S  0.0  0.2   0:00.00 privoxy            
 5480 root      20   0 10572  916  372 S  0.0  0.2   0:00.02 winbindd           
 5487 root      20   0 10572  772  228 S  0.0  0.2   0:00.00 winbindd           
 5507 root      20   0  2540  756  588 S  0.0  0.2   0:00.00 xinetd             
 5562 root      20   0  3328  580  392 S  0.0  0.1   0:00.04 hald-runner        
 5614 root      20   0  5176  608  400 S  0.0  0.1   0:00.04 hald-addon-inpu    
 5644 haldaemo  20   0  5032  812  592 S  0.0  0.2   0:00.00 hald-addon-acpi    
 5664 root      20   0 16116 1172  424 S  0.0  0.2   0:00.00 gdm                
 5669 root      20   0 16688 1716  756 S  0.0  0.4   0:00.02 gdm                
 5695 root      20   0  4304  836  540 S  0.0  0.2   0:00.06 wpa_supplicant     
 5764 root      20   0  6100 1424  780 S  0.0  0.3   0:00.00 cupsd              
 5801 root      20   0  4324  488  264 S  0.0  0.1   0:00.00 system-tools-ba    
 5860 root      20   0  2032  852  720 S  0.0  0.2   0:00.00 anacron            
 5876 daemon    20   0  2096  432  304 S  0.0  0.1   0:00.00 atd                
 5904 root      20   0  4540  940  732 S  0.0  0.2   0:00.00 cron               
 6069 jkerr     20   0 27600 2536  964 S  0.0  0.5   0:00.24 gnome-session      
 6135 jkerr     20   0  4812  516  196 S  0.0  0.1   0:00.02 ssh-agent          
 6138 jkerr     20   0  3144  508  272 S  0.0  0.1   0:00.00 dbus-launch        
 6139 jkerr     20   0  3068 1008  372 S  0.0  0.2   0:00.18 dbus-daemon        
 6145 jkerr     20   0  7840 1228  720 S  0.0  0.3   0:00.00 gconf-helper       
 6159 jkerr     20   0 20156 2380  604 S  0.0  0.5   0:00.12 seahorse-agent     
 6162 jkerr     20   0  6684 1064  736 S  0.0  0.2   0:00.02 gvfsd              
 6167 jkerr     20   0 29584 1184  712 S  0.0  0.2   0:00.00 gvfs-fuse-daemo    
 6174 jkerr     20   0 31820 4372  772 S  0.0  0.9   0:01.02 gnome-settings-    
 6184 jkerr     20   0 69140  12m 1268 S  0.0  2.7   0:07.45 gnome-panel        
 6187 jkerr     20   0 41900 1656  800 S  0.0  0.3   0:00.18 bonobo-activati    
 6195 jkerr     20   0 68584 3364  988 S  0.0  0.7   0:00.12 evolution-alarm    
 6197 jkerr     20   0 28940 7108  952 D  0.0  1.5   0:00.34 python             
 6204 jkerr     20   0 79584 9876  864 S  0.0  2.0   0:02.59 nm-applet          
 6212 jkerr     20   0 36332 4096  856 S  0.0  0.8   0:00.50 notify-osd         
 6213 jkerr     20   0 26428 3540  668 S  0.0  0.7   0:00.20 gnome-power-man    
 6240 root      20   0  1808  516  444 S  0.0  0.1   0:00.00 getty              
 6297 jkerr     20   0 23900 2596  964 S  0.0  0.5   0:10.70 bubblemon-gnome    
 6300 jkerr     20   0 23980 2632  948 S  0.0  0.5   0:00.10 gtodo-applet       
 6309 jkerr     20   0  6688 1108  800 S  0.0  0.2   0:00.00 gvfsd-burn         
 6317 jkerr     20   0 43740 5140  992 S  0.0  1.1   0:00.82 stickynotes_app    
 6331 jkerr     20   0 41300 4124  904 S  0.0  0.9   0:00.32 trashapplet        
 6334 jkerr     20   0 61636 5956 1184 S  0.0  1.2   0:00.42 mixer_applet2      
 6337 jkerr     20   0 43812 4892 1080 S  0.0  1.0   0:00.44 fast-user-switc    
 6383 jkerr     20   0 17752 1356  144 S  0.0  0.3   0:01.60 gnome-screensav    
 6385 jkerr     20   0 50804 7068  892 S  0.0  1.5   0:01.76 gnome-terminal     
 6389 jkerr     20   0 44980 3236  952 S  0.0  0.7   0:00.10 evolution-excha    
 6390 jkerr     20   0  2036  684  560 S  0.0  0.1   0:00.00 gnome-pty-helpe    
 6391 jkerr     20   0  7820 3300  716 S  0.0  0.7   0:00.16 bash               
 6420 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2          
 6433 jkerr     20   0 79252 2996  924 S  0.0  0.6   0:00.06 evolution-data-    
 6488 root      20   0  5180  664  452 D  0.0  0.1   0:00.08 hald-addon-stor    
 6490 root      20   0  5180  664  452 D  0.0  0.1   0:00.08 hald-addon-stor    
 6530 root      20   0 13624 6112  788 S  0.0  1.3   0:00.14 system-service-    
 6700 jkerr     20   0 15200 1224  812 S  0.0  0.3   0:00.02 gvfsd-computer     
 6937 jkerr     20   0  2956  412  312 S  0.0  0.1   0:00.00 operapluginclea    
 6987 root      20   0  1872  424  356 S  0.0  0.1   0:00.00 sh                 
 6988 root      30  10  1792  588  432 S  0.0  0.1   0:00.00 run-parts          
 7000 root      30  10  1872  468  388 S  0.0  0.1   0:00.00 apt                
 7035 jkerr     20   0  7820 3304  716 S  0.0  0.7   0:00.18 bash               
 7241 jkerr     20   0  1872  436  372 S  0.0  0.1   0:00.00 manview            
 7453 root      30  10 73120  62m  956 D  0.0 13.3   0:05.90 update-apt-xapi    
 7576 root      30  10  1808  380  316 S  0.0  0.1   0:00.00 cat                
 7611 jkerr     20   0  2452 1040  748 R  0.0  0.2   0:00.60 top                
 7688 jkerr     20   0  7248 2684  708 S  0.0  0.6   0:00.14 bash               
 7708 jkerr     20   0  7248 2068   92 S  0.0  0.4   0:00.00 bash               
 7709 jkerr     20   0  7248 2056   80 S  0.0  0.4   0:00.00 bash               
 7710 jkerr     20   0  7248 2060   84 S  0.0  0.4   0:00.00 bash

---

