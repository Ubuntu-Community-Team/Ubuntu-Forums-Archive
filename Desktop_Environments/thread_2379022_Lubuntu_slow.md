---
title: "Lubuntu slow"
date: 2017-11-30
forum: Desktop Environments
---

### Post by ancienthero on 2017-11-30
Hi everybody,

I am sorry to make this new thread, because I have seen that this question has been made over and over again, but I could not find a solution for the problem.
I will try to give you more infos as I can

The specs of my notebook

Model: HP - Dv6-1150el Moonlight K29 (It is 8 years old)
Processor type: Intel Core 2 Duo
Processor name: T9550
Processor speed: 2.66 GHz
RAM: 4GB
Video: ATI Radeon HD4650

First question: are those specs enough to run Lubuntu?

Now, you will ask  'What do you mean with "slow"?'
Well, about everything is slow :( Booting (but I don't care about it, I can wait for it), navigating through directories, opening menus of applications (also opening the "start" menu), switching from one tab to another of Chrome, using Libreoffice. Even when I use the terminal, if I use the TAB to autocomplete it takes a bit to show output...

I used htop and free to monitor the situation and I see that RAM is never full and swap is never used
```

eriol@pcchio:~$ free -m
                total        used        free      shared  buff/cache   available
Mem:           3915        1137        1382         130        1395        2400
Swap:          8255           0        8255

```

Another thing that is really strange is that randomly (and that's why I can not understand what's going on) everything runs fast as it should. I can notice the difference just after booting: the notebook runs slow or the notebook runs fast...

Any advice is accepted. 

Thank you

---

### Post by ajgreeny on 2017-11-30
That machine should run Lubuntu very well, so something is obviously going wrong.  Which version of Lubuntu are you using?

I note that the ram usage is high for Lubuntu so wonder if you have some tasks running in the background that are using resources that you're not aware of.

At some point when it is running slow have a look at the output of **top** in terminal to see what is using all the resources.  You can sort the output of top by hitting upper case C or M to see CPU or Memory highest use listed first.

You can add an option to the top command to save the output as a text file and then copy the content of that back here for others to look at.
Try ```
top -n 1 > top.txt
``` and then copy that top.txt back here in **code tags** (see my signature below for a How-To)

---

### Post by vasa1 on 2017-11-30
```
top -n1 -o %MEM
```or```
top -n1 -o %CPU
```are useful as well. After installing *inxi*, you could post```
inxi -Fxz
```.

And what does```
ls /usr/share/xessions
```show?

---

### Post by ancienthero on 2017-11-30
```
top -n1 -o %MEM
```

```

top - 12:18:06 up  4:06,  1 user,  load average: 0,26, 0,46, 0,46
Tasks: 156 total,   1 running, 155 sleeping,   0 stopped,   0 zombie
%Cpu(s):  6,6 us,  1,7 sy,  0,0 ni, 69,0 id, 22,6 wa,  0,0 hi,  0,0 si,  0,0 st
KiB Mem :  4009960 total,   488404 free,  1845736 used,  1675820 buff/cache
KiB Swap:  8454140 total,  8454140 free,        0 used.  1759392 avail Mem 


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
11437 eriol     20   0 3917600 533048  46556 S   0,0 13,3   0:34.97 java        
 1572 eriol     20   0 1648184 335092 154008 S   0,0  8,4   6:20.82 chrome      
 2050 eriol     20   0 1441756 300864 153568 S   0,0  7,5   2:15.61 chrome      
 7027 eriol     20   0 1843220 244384  76760 S   0,0  6,1   0:20.98 chrome      
 1713 eriol     20   0 1398632 202548  58012 S   0,0  5,1   0:30.24 chrome      
 7054 eriol     20   0 1330624 193848  74620 S   0,0  4,8   2:10.73 chrome      
 3680 eriol     20   0 1437500 191492  86508 S  12,5  4,8   6:02.12 chrome      
11356 eriol     20   0 1007520 184020 108700 S   0,0  4,6   0:02.33 soffice.bin 
10651 eriol     20   0 1278944 181236  81404 S   0,0  4,5   0:13.04 chrome      
 9129 eriol     20   0 1200604 139164  81796 S   0,0  3,5   0:06.62 chrome      
 1753 eriol     20   0  472140  63712  42944 S   0,0  1,6   0:01.00 chrome      
  652 root      20   0  529352  59468  38964 S   0,0  1,5   4:11.67 Xorg        
 1581 eriol     20   0  434104  53988  44104 S   0,0  1,3   0:00.20 chrome      
 1299 eriol     20   0  738240  34416  27800 S   0,0  0,9   0:02.62 nm-applet   
 1287 eriol     20   0  694996  34060  24436 S   0,0  0,8   0:05.17 pcmanfm     
 1407 eriol     20   0  550596  33392  27216 S   0,0  0,8   0:00.95 xpad        
 1284 eriol     20   0 1104200  33024  24304 S   0,0  0,8   0:16.11 lxpanel

```

```
top -n1 -o %CPU
```

```

top - 12:18:53 up  4:07,  1 user,  load average: 0,17, 0,41, 0,44
Tasks: 156 total,   1 running, 155 sleeping,   0 stopped,   0 zombie
%Cpu(s):  6,6 us,  1,7 sy,  0,0 ni, 69,1 id, 22,6 wa,  0,0 hi,  0,0 si,  0,0 st
KiB Mem :  4009960 total,   466324 free,  1867236 used,  1676400 buff/cache
KiB Swap:  8454140 total,  8454140 free,        0 used.  1737380 avail Mem 


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 3680 eriol     20   0 1438012 192956  87020 S   5,9  4,8   6:07.93 chrome      
11437 eriol     20   0 3917600 533348  46624 S   5,9 13,3   0:35.57 java        
13044 eriol     20   0   46348   3932   3368 R   5,9  0,1   0:00.02 top         
    1 root      20   0  154804   8764   6484 S   0,0  0,2   0:02.95 systemd     
    2 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kthreadd    
    4 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/0:+ 
    6 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 mm_percpu_+ 
    7 root      20   0       0      0      0 S   0,0  0,0   0:00.26 ksoftirqd/0 
    8 root      20   0       0      0      0 S   0,0  0,0   0:03.15 rcu_sched   
    9 root      20   0       0      0      0 S   0,0  0,0   0:00.00 rcu_bh      
   10 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 migration/0 
   11 root      rt   0       0      0      0 S   0,0  0,0   0:00.02 watchdog/0  
   12 root      20   0       0      0      0 S   0,0  0,0   0:00.00 cpuhp/0     
   13 root      20   0       0      0      0 S   0,0  0,0   0:00.00 cpuhp/1     
   14 root      rt   0       0      0      0 S   0,0  0,0   0:00.02 watchdog/1  
   15 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 migration/1 
   16 root      20   0       0      0      0 S   0,0  0,0   0:00.25 ksoftirqd/1

```

```
inxi -Fxz
```

```

System:    Host: pcchio Kernel: 4.13.0-17-generic x86_64 bits: 64 gcc: 7.2.0
           Desktop: LXDE (Openbox 3.6.1) Distro: Ubuntu 17.10
Machine:   Device: laptop System: Hewlett-Packard product: HP Pavilion dv6 Notebook PC v: Rev 1 serial: N/A
           Mobo: Hewlett-Packard model: 3628 v: 18.51 serial: N/A
           BIOS: Hewlett-Packard v: F.46 date: 08/25/2011
CPU:       Dual core Intel Core2 Duo T9550 (-MCP-) 
           arch: Penryn rev.10 cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 10641
           clock speeds: max: 2667 MHz 1: 2660 MHz 2: 2660 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] RV730/M96 [Mobility Radeon HD 4650/5165]
           bus-ID: 01:00.0
           Display Server: x11 (X.Org 1.19.5 )
           drivers: ati,radeon (unloaded: modesetting,fbdev,vesa)
           Resolution: 1366x768@59.97hz
           OpenGL: renderer: AMD RV730 (DRM 2.50.0 / 4.13.0-17-generic, LLVM 5.0.0)
           version: 3.3 Mesa 17.2.2 Direct Render: Yes
Audio:     Card-1 Advanced Micro Devices [AMD/ATI] RV710/730 HDMI Audio [Radeon HD 4000 series]
           driver: snd_hda_intel bus-ID: 01:00.1
           Card-2 Intel 82801I (ICH9 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.13.0-17-generic
Network:   Card-1: Intel PRO/Wireless 5100 AGN [Shiloh] Network Connection
           driver: iwlwifi bus-ID: 02:00.0
           IF: wlp2s0 state: up mac: <filter>
           Card-2: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: 5000 bus-ID: 03:00.0
           IF: enp3s0 state: down mac: <filter>
Drives:    HDD Total Size: 500.1GB (15.1% used)
           ID-1: /dev/sdb model: TOSHIBA_MK5055GS size: 500.1GB temp: 0C
Partition: ID-1: / size: 450G used: 63G (15%) fs: ext4 dev: /dev/sdb1
           ID-2: swap-1 size: 8.66GB used: 0.00GB (0%)
           fs: swap dev: /dev/sdb2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 57.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 159 Uptime: 4:08 Memory: 1917.4/3916.0MB
           Init: systemd runlevel: 5 Gcc sys: 7.2.0
           Client: Shell (bash 4.4.121) inxi: 2.3.37 

```

```
ls /usr/share/xessions
```

```
Lubuntu.desktop  Lubuntu-Netbook.desktop  lxqt.desktop  openbox.desktop
```

As you can see from inxi output, I have the latest version of Lubuntu. I tried to make a fresh install, because I had this probblem also before (Lubuntu 04.17).

Note: while writing everithing is running fast(and I have a lot of "things" running. Chrome, Eclipse, Libreoffice...). I will try to give you the outputs when it will go slow once again

---

### Post by vasa1 on 2017-11-30
```
clock speeds: max: 2667 MHz 1: 2660 MHz 2: 2660 MHz
```Does that mean your CPU cores are pretty close to maxing out?

Have you turned off hardware acceleration in your Chrome browser? Are you using any script blocker with your browser? These steps may help your browser use fewer resources.

---

### Post by ancienthero on 2017-11-30
> **vasa1 said:**
> ```
clock speeds: max: 2667 MHz 1: 2660 MHz 2: 2660 MHz
```Does that mean your CPU cores are pretty close to maxing out?


Don't know, but I see that 1 and 2 in inxi output are always the same

> **vasa1 said:**
> Have you turned off hardware acceleration in your Chrome browser?

Did it this afternoon

> **vasa1 said:**
> Are you using any script blocker with your browser?

AdBlock

> **vasa1 said:**
> These steps may help your browser use fewer resources.

I have not disabled AdBlock, but I feel a little enhancement. Anyway there are still this kind of freeze seconds

```
top -n1 -o %MEM
```


```
top - 17:12:43 up 7 min,  1 user,  load average: 3,37, 3,08, 1,56
Tasks: 156 total,   1 running, 155 sleeping,   0 stopped,   0 zombie
%Cpu(s):  9,3 us,  3,3 sy,  0,3 ni, 30,2 id, 56,8 wa,  0,0 hi,  0,1 si,  0,0 st
KiB Mem :  4009960 total,  2161420 free,  1008960 used,   839580 buff/cache
KiB Swap:  8454140 total,  8454140 free,        0 used.  2689744 avail Mem 


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 2857 eriol     20   0 1996328 302272  93496 S   0,0  7,5   0:18.90 chrome
 2111 eriol     20   0 1515844 269060 131576 S   0,0  6,7   0:30.39 chrome
 3015 eriol     20   0 1300988 207236 105772 S   0,0  5,2   0:08.44 chrome
 2802 eriol     20   0 1321072 189268  56344 S   0,0  4,7   0:08.31 chrome
 2975 eriol     20   0  907264 152792 101368 S   0,0  3,8   0:01.11 soffice.bin
 2927 eriol     20   0 1237708 145656  75808 S   0,0  3,6   0:03.05 chrome
 3542 eriol     20   0 1178940 119540  74108 S   0,0  3,0   0:04.41 chrome
 2831 eriol     20   0  475348  66960  42680 S   0,0  1,7   0:00.09 chrome
 2120 eriol     20   0  434104  53912  44032 S   0,0  1,3   0:00.16 chrome
  640 root      20   0  516328  52868  37608 S  13,3  1,3   0:09.22 Xorg
  850 eriol     20   0  665596  36812  30084 S   0,0  0,9   0:00.16 nm-applet
  836 eriol     20   0  760260  34412  24512 S   6,7  0,9   0:01.82 pcmanfm
  927 eriol     20   0  400772  32988  27052 S   0,0  0,8   0:00.12 xpad
  827 eriol     20   0  904684  30584  24172 D   0,0  0,8   0:00.91 lxpanel
 1059 eriol     20   0  519708  26420  21556 S   0,0  0,7   0:00.32 lxterminal
  864 eriol     20   0  592964  24512  19892 S   0,0  0,6   0:00.07 update-not+
  944 eriol     20   0  426456  22912  18576 S   0,0  0,6   0:00.05 light-lock+
  837 eriol     20   0  382044  22028  18096 S   0,0  0,5   0:00.06 xfce4-powe+
  823 eriol     20   0  393064  21120  16872 S   0,0  0,5   0:00.15 openbox
  873 eriol     20   0  439040  20348  17848 S   0,0  0,5   0:00.02 xfce4-noti+
  542 root      20   0  488576  18132  14992 S   0,0  0,5   0:00.21 NetworkMan+
  643 colord    20   0  332320  15608  10520 S   0,0  0,4   0:00.12 colord
  551 root      20   0  467048  15408   9580 S   0,0  0,4   0:00.02 snapd
 1025 eriol     20   0  780640  15368  13156 S   0,0  0,4   0:00.03 indicator-+
  743 eriol     20   0  371992  15196  13240 S   0,0  0,4   0:00.07 lxsession
  845 eriol     20   0  297292  12788  11336 S   0,0  0,3   0:00.00 lxpolkit
  671 whoopsie  20   0  461472  12640  10792 S   0,0  0,3   0:00.01 whoopsie
 2124 eriol     20   0  434104  12528   2640 S   0,0  0,3   0:00.02 chrome
 2833 eriol     20   0  402264  12176   2508 S   0,0  0,3   0:00.00 chrome
 1000 eriol     20   0  888624  11552   8476 S   0,0  0,3   0:00.27 pulseaudio
  600 root      20   0  311864  11492   8312 S   0,0  0,3   0:00.08 polkitd
  555 root      20   0  463820  10880   8420 S   0,0  0,3   0:00.12 udisksd
  885 eriol     20   0  312780  10660   9144 S   0,0  0,3   0:00.01 gvfs-udisk+
  851 eriol     20   0  164488  10208   8968 S   0,0  0,3   0:00.00 xfce4-powe+
  974 eriol     20   0  376748  10040   8752 S   0,0  0,3   0:00.02 gvfsd-trash
  547 root      20   0  427552   9296   7420 S   0,0  0,2   0:00.04 ModemManag+
  544 root      20   0  102776   9264   6844 S   0,0  0,2   0:00.04 cupsd
  629 root      20   0  308368   9048   7784 S   0,0  0,2   0:00.02 lightdm
  554 root      20   0  301360   8928   7780 S   0,0  0,2   0:00.05 accounts-d+
  879 root      20   0  312088   8900   7508 S   0,0  0,2   0:00.15 upowerd
 1027 eriol     20   0  443076   8544   7456 S   0,0  0,2   0:00.02 indicator-+
    1 root      20   0  154440   8452   6492 S   0,0  0,2   0:01.93 systemd
 2121 eriol     20   0  121452   7888   6688 S   0,0  0,2   0:00.00 nacl_helper
  737 eriol     20   0   80244   7808   6592 S   0,0  0,2   0:00.04 systemd
  940 eriol     20   0  207964   7660   6904 S   0,0  0,2   0:00.00 menu-cached
  905 eriol     20   0  368392   7636   6780 S   0,0  0,2   0:00.00 gvfs-afc-v+
  812 eriol     20   0  431604   7600   6736 S   0,0  0,2   0:00.00 gvfsd-fuse
  732 root      20   0  245964   7052   6016 S   0,0  0,2   0:00.01 lightdm
  807 eriol     20   0  284864   7020   6148 S   0,0  0,2   0:00.02 gvfsd
  659 root      20   0   48836   6696   6016 S   0,0  0,2   0:00.02 wpa_suppli+
  246 root      20   0   62056   6592   5916 S   0,0  0,2   0:00.26 systemd-jo+
 2958 eriol     20   0  210628   6172   5024 S   0,0  0,2   0:00.00 oosplash
  947 eriol     20   0  281560   6072   5240 S   0,0  0,2   0:00.00 gvfs-gphot+
  951 eriol     20   0  267000   6044   5440 S   0,0  0,2   0:00.00 gvfs-goa-v+
  261 root      20   0   47228   5960   3112 S   0,0  0,1   0:01.21 systemd-ud+
  616 systemd+  20   0   65848   5928   5204 S   0,0  0,1   0:00.12 systemd-re+
  541 root      20   0   65672   5896   5144 S   0,0  0,1   0:00.03 systemd-lo+
  635 root      20   0   72136   5624   4900 S   0,0  0,1   0:00.01 sshd
 1061 eriol     20   0   22984   5620   3624 S   0,0  0,1   0:00.03 bash
  930 eriol     20   0  268928   5512   4808 S   0,0  0,1   0:00.01 gvfs-mtp-v+
  957 eriol     20   0  187776   5168   4536 S   0,0  0,1   0:00.00 dconf-serv+
  862 eriol     20   0   58932   5048   4536 S   0,0  0,1   0:00.00 xfconfd
  514 message+  20   0   48268   4892   3612 S   0,0  0,1   0:00.18 dbus-daemon
  305 systemd+  20   0  145312   4864   4296 S   0,0  0,1   0:00.01 systemd-ti+
  759 eriol     20   0   47828   4468   3688 S   0,0  0,1   0:00.05 dbus-daemon
 3595 eriol     20   0   46360   3896   3360 R   6,7  0,1   0:00.01 top
  537 syslog    20   0  256536   3808   2868 S   0,0  0,1   0:00.03 rsyslogd
  844 root      20   0   16228   3724   2860 S   0,0  0,1   0:00.00 dhclient
  539 avahi     20   0   49464   3444   3084 S   0,0  0,1   0:00.01 avahi-daem+
  545 root      20   0   38564   3420   3072 S   0,0  0,1   0:00.00 irqbalance
 3593 eriol     20   0   12760   3216   2996 S   0,0  0,1   0:00.00 monitoring+
  540 root      20   0   31244   3148   2864 S   0,0  0,1   0:00.00 cron
  677 kernoops  20   0   56744   2592   2148 S   0,0  0,1   0:00.00 kerneloops
  738 eriol     20   0  104200   2108     60 S   0,0  0,1   0:00.00 (sd-pam)
 1060 eriol     20   0   14980   1992   1832 S   0,0  0,0   0:00.00 gnome-pty-+
  628 root      20   0   16124   1972   1832 S   0,0  0,0   0:00.00 agetty
  546 root      20   0    4500    844    772 S   0,0  0,0   0:00.00 acpid
 2117 eriol     20   0    7556    720    648 S   0,0  0,0   0:00.00 cat
 2116 eriol     20   0    7556    716    644 S   0,0  0,0   0:00.00 cat
  549 avahi     20   0   49332    360      0 S   0,0  0,0   0:00.00 avahi-daem+
  857 eriol     20   0   11228    324      0 S   0,0  0,0   0:00.00 ssh-agent
  796 eriol     20   0   11228    320      0 S   0,0  0,0   0:00.00 ssh-agent
    2 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kthreadd
    3 root      20   0       0      0      0 S   0,0  0,0   0:00.04 kworker/0:0
    4 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/0:+
    5 root      20   0       0      0      0 S   0,0  0,0   0:01.45 kworker/u8+
    6 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 mm_percpu_+
    7 root      20   0       0      0      0 S   0,0  0,0   0:00.03 ksoftirqd/0
    8 root      20   0       0      0      0 S   0,0  0,0   0:00.18 rcu_sched
    9 root      20   0       0      0      0 S   0,0  0,0   0:00.00 rcu_bh
   10 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 migration/0
   11 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 watchdog/0
   12 root      20   0       0      0      0 S   0,0  0,0   0:00.00 cpuhp/0
   13 root      20   0       0      0      0 S   0,0  0,0   0:00.00 cpuhp/1
   14 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 watchdog/1
   15 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 migration/1
   16 root      20   0       0      0      0 S   0,0  0,0   0:00.02 ksoftirqd/1
   17 root      20   0       0      0      0 S   0,0  0,0   0:00.26 kworker/1:0
   18 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/1:+
   19 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kdevtmpfs
   20 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 netns
   21 root      20   0       0      0      0 S   0,0  0,0   0:00.68 kworker/1:1
   22 root      20   0       0      0      0 S   0,0  0,0   0:00.09 kworker/0:1
   23 root      20   0       0      0      0 S   0,0  0,0   0:00.00 khungtaskd
   24 root      20   0       0      0      0 S   0,0  0,0   0:00.00 oom_reaper
   25 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 writeback
   26 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kcompactd0
   27 root      25   5       0      0      0 S   0,0  0,0   0:00.00 ksmd
   28 root      39  19       0      0      0 S   0,0  0,0   0:00.00 khugepaged
   29 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 crypto
   30 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kintegrityd
   31 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kblockd
   32 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 ata_sff
   33 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 md
   34 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 edac-poller
   35 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 devfreq_wq
   36 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 watchdogd
   38 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kauditd
   39 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kswapd0
   40 root      20   0       0      0      0 S   0,0  0,0   0:00.00 ecryptfs-k+
   82 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kthrotld
   83 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 acpi_therm+
   93 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 ipv6_addrc+
  118 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 charger_ma+
  168 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 firewire
  169 root     -51   0       0      0      0 S   0,0  0,0   0:00.00 irq/16-mmc0
  170 root      20   0       0      0      0 S   0,0  0,0   0:00.00 scsi_eh_0
  171 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 scsi_tmf_0
  172 root      20   0       0      0      0 S   0,0  0,0   0:00.00 scsi_eh_1
  173 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 scsi_tmf_1
  174 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 firewire_o+
  175 root      20   0       0      0      0 S   0,0  0,0   0:00.00 scsi_eh_2
  176 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 scsi_tmf_2
  177 root      20   0       0      0      0 S   0,0  0,0   0:00.06 kworker/0:2
  178 root      20   0       0      0      0 S   0,0  0,0   0:00.00 scsi_eh_3
  179 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 scsi_tmf_3
  181 root      20   0       0      0      0 S   0,0  0,0   0:00.00 scsi_eh_4
  182 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 scsi_tmf_4
  183 root      20   0       0      0      0 S   0,0  0,0   0:00.00 scsi_eh_5
  184 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 scsi_tmf_5
  185 root      20   0       0      0      0 S   0,0  0,0   0:00.02 kworker/u8+
  186 root      20   0       0      0      0 S   0,0  0,0   0:00.04 kworker/u8+
  190 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 ttm_swap
  195 root       0 -20       0      0      0 S   0,0  0,0   0:00.08 kworker/1:+
  196 root       0 -20       0      0      0 S   0,0  0,0   0:00.01 kworker/0:+
  216 root      20   0       0      0      0 S   0,0  0,0   0:00.05 jbd2/sda1-8
  217 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 ext4-rsv-c+
  316 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 cfg80211
  318 root     -51   0       0      0      0 S   0,0  0,0   0:00.30 irq/33-iwl+
  319 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/u9+
  323 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kmemstick
  329 root      20   0       0      0      0 S   0,0  0,0   0:00.00 rc0
  657 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/u9+
 2894 root      20   0       0      0      0 S   0,0  0,0   0:00.07 kworker/0:3
 3538 root      20   0       0      0      0 S   0,0  0,0   0:00.03 kworker/1:2
 3589 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kworker/u8+
```


```
top -n1 -o %CPU
```


```
top - 17:12:44 up 7 min,  1 user,  load average: 3,37, 3,08, 1,56
Tasks: 156 total,   1 running, 155 sleeping,   0 stopped,   0 zombie
%Cpu(s):  9,3 us,  3,3 sy,  0,3 ni, 30,3 id, 56,8 wa,  0,0 hi,  0,1 si,  0,0 st
KiB Mem :  4009960 total,  2160884 free,  1009484 used,   839592 buff/cache
KiB Swap:  8454140 total,  8454140 free,        0 used.  2689220 avail Mem 


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
  836 eriol     20   0  760260  34412  24512 S   6,2  0,9   0:01.83 pcmanfm
 3599 eriol     20   0   46360   3744   3208 R   6,2  0,1   0:00.01 top
    1 root      20   0  154440   8452   6492 S   0,0  0,2   0:01.93 systemd
    2 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kthreadd
    3 root      20   0       0      0      0 S   0,0  0,0   0:00.04 kworker/0:0
    4 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/0:+
    5 root      20   0       0      0      0 S   0,0  0,0   0:01.45 kworker/u8+
    6 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 mm_percpu_+
    7 root      20   0       0      0      0 S   0,0  0,0   0:00.03 ksoftirqd/0
    8 root      20   0       0      0      0 S   0,0  0,0   0:00.18 rcu_sched
    9 root      20   0       0      0      0 S   0,0  0,0   0:00.00 rcu_bh
   10 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 migration/0
   11 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 watchdog/0
   12 root      20   0       0      0      0 S   0,0  0,0   0:00.00 cpuhp/0
   13 root      20   0       0      0      0 S   0,0  0,0   0:00.00 cpuhp/1
   14 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 watchdog/1
   15 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 migration/1
   16 root      20   0       0      0      0 S   0,0  0,0   0:00.02 ksoftirqd/1
   17 root      20   0       0      0      0 S   0,0  0,0   0:00.26 kworker/1:0
   18 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/1:+
   19 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kdevtmpfs
   20 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 netns
   21 root      20   0       0      0      0 S   0,0  0,0   0:00.68 kworker/1:1
   22 root      20   0       0      0      0 S   0,0  0,0   0:00.09 kworker/0:1
   23 root      20   0       0      0      0 S   0,0  0,0   0:00.00 khungtaskd
   24 root      20   0       0      0      0 S   0,0  0,0   0:00.00 oom_reaper
   25 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 writeback
   26 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kcompactd0
   27 root      25   5       0      0      0 S   0,0  0,0   0:00.00 ksmd
   28 root      39  19       0      0      0 S   0,0  0,0   0:00.00 khugepaged
   29 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 crypto
   30 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kintegrityd
   31 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kblockd
   32 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 ata_sff
   33 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 md
   34 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 edac-poller
   35 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 devfreq_wq
   36 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 watchdogd
   38 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kauditd
   39 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kswapd0
   40 root      20   0       0      0      0 S   0,0  0,0   0:00.00 ecryptfs-k+
   82 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kthrotld
   83 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 acpi_therm+
   93 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 ipv6_addrc+
  118 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 charger_ma+
  168 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 firewire
  169 root     -51   0       0      0      0 S   0,0  0,0   0:00.00 irq/16-mmc0
  170 root      20   0       0      0      0 S   0,0  0,0   0:00.00 scsi_eh_0
  171 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 scsi_tmf_0
  172 root      20   0       0      0      0 S   0,0  0,0   0:00.00 scsi_eh_1
  173 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 scsi_tmf_1
  174 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 firewire_o+
  175 root      20   0       0      0      0 S   0,0  0,0   0:00.00 scsi_eh_2
  176 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 scsi_tmf_2
  177 root      20   0       0      0      0 S   0,0  0,0   0:00.06 kworker/0:2
  178 root      20   0       0      0      0 S   0,0  0,0   0:00.00 scsi_eh_3
  179 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 scsi_tmf_3
  181 root      20   0       0      0      0 S   0,0  0,0   0:00.00 scsi_eh_4
  182 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 scsi_tmf_4
  183 root      20   0       0      0      0 S   0,0  0,0   0:00.00 scsi_eh_5
  184 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 scsi_tmf_5
  185 root      20   0       0      0      0 S   0,0  0,0   0:00.02 kworker/u8+
  186 root      20   0       0      0      0 S   0,0  0,0   0:00.04 kworker/u8+
  190 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 ttm_swap
  195 root       0 -20       0      0      0 S   0,0  0,0   0:00.08 kworker/1:+
  196 root       0 -20       0      0      0 S   0,0  0,0   0:00.01 kworker/0:+
  216 root      20   0       0      0      0 S   0,0  0,0   0:00.05 jbd2/sda1-8
  217 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 ext4-rsv-c+
  246 root      20   0   62056   6592   5916 S   0,0  0,2   0:00.26 systemd-jo+
  261 root      20   0   47228   5960   3112 S   0,0  0,1   0:01.21 systemd-ud+
  305 systemd+  20   0  145312   4864   4296 S   0,0  0,1   0:00.01 systemd-ti+
  316 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 cfg80211
  318 root     -51   0       0      0      0 S   0,0  0,0   0:00.30 irq/33-iwl+
  319 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/u9+
  323 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kmemstick
  329 root      20   0       0      0      0 S   0,0  0,0   0:00.00 rc0
  514 message+  20   0   48268   4892   3612 S   0,0  0,1   0:00.18 dbus-daemon
  537 syslog    20   0  256536   3808   2868 S   0,0  0,1   0:00.03 rsyslogd
  539 avahi     20   0   49464   3444   3084 S   0,0  0,1   0:00.01 avahi-daem+
  540 root      20   0   31244   3148   2864 S   0,0  0,1   0:00.00 cron
  541 root      20   0   65672   5896   5144 S   0,0  0,1   0:00.03 systemd-lo+
  542 root      20   0  488576  18132  14992 S   0,0  0,5   0:00.21 NetworkMan+
  544 root      20   0  102776   9264   6844 S   0,0  0,2   0:00.04 cupsd
  545 root      20   0   38564   3420   3072 S   0,0  0,1   0:00.00 irqbalance
  546 root      20   0    4500    844    772 S   0,0  0,0   0:00.00 acpid
  547 root      20   0  427552   9296   7420 S   0,0  0,2   0:00.04 ModemManag+
  549 avahi     20   0   49332    360      0 S   0,0  0,0   0:00.00 avahi-daem+
  551 root      20   0  467048  15408   9580 S   0,0  0,4   0:00.02 snapd
  554 root      20   0  301360   8928   7780 S   0,0  0,2   0:00.05 accounts-d+
  555 root      20   0  463820  10880   8420 S   0,0  0,3   0:00.12 udisksd
  600 root      20   0  311864  11492   8312 S   0,0  0,3   0:00.08 polkitd
  616 systemd+  20   0   65848   5928   5204 S   0,0  0,1   0:00.12 systemd-re+
  628 root      20   0   16124   1972   1832 S   0,0  0,0   0:00.00 agetty
  629 root      20   0  308368   9048   7784 S   0,0  0,2   0:00.02 lightdm
  635 root      20   0   72136   5624   4900 S   0,0  0,1   0:00.01 sshd
  640 root      20   0  516200  52868  37608 S   0,0  1,3   0:09.22 Xorg
  643 colord    20   0  332320  15608  10520 S   0,0  0,4   0:00.12 colord
  657 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/u9+
  659 root      20   0   48836   6696   6016 S   0,0  0,2   0:00.02 wpa_suppli+
  671 whoopsie  20   0  461472  12640  10792 S   0,0  0,3   0:00.01 whoopsie
  677 kernoops  20   0   56744   2592   2148 S   0,0  0,1   0:00.00 kerneloops
  732 root      20   0  245964   7052   6016 S   0,0  0,2   0:00.01 lightdm
  737 eriol     20   0   80244   7808   6592 S   0,0  0,2   0:00.04 systemd
  738 eriol     20   0  104200   2108     60 S   0,0  0,1   0:00.00 (sd-pam)
  743 eriol     20   0  371992  15196  13240 S   0,0  0,4   0:00.07 lxsession
  759 eriol     20   0   47828   4468   3688 S   0,0  0,1   0:00.05 dbus-daemon
  796 eriol     20   0   11228    320      0 S   0,0  0,0   0:00.00 ssh-agent
  807 eriol     20   0  284864   7020   6148 S   0,0  0,2   0:00.02 gvfsd
  812 eriol     20   0  431604   7600   6736 S   0,0  0,2   0:00.00 gvfsd-fuse
  823 eriol     20   0  393064  21120  16872 S   0,0  0,5   0:00.15 openbox
  827 eriol     20   0  904684  30584  24172 D   0,0  0,8   0:00.91 lxpanel
  837 eriol     20   0  382044  22028  18096 S   0,0  0,5   0:00.06 xfce4-powe+
  844 root      20   0   16228   3724   2860 S   0,0  0,1   0:00.00 dhclient
  845 eriol     20   0  297292  12788  11336 S   0,0  0,3   0:00.00 lxpolkit
  850 eriol     20   0  665596  36812  30084 S   0,0  0,9   0:00.16 nm-applet
  851 eriol     20   0  164488  10208   8968 S   0,0  0,3   0:00.00 xfce4-powe+
  857 eriol     20   0   11228    324      0 S   0,0  0,0   0:00.00 ssh-agent
  862 eriol     20   0   58932   5048   4536 S   0,0  0,1   0:00.00 xfconfd
  864 eriol     20   0  592964  24512  19892 S   0,0  0,6   0:00.07 update-not+
  873 eriol     20   0  439040  20348  17848 S   0,0  0,5   0:00.02 xfce4-noti+
  879 root      20   0  312088   8900   7508 S   0,0  0,2   0:00.15 upowerd
  885 eriol     20   0  312780  10660   9144 S   0,0  0,3   0:00.01 gvfs-udisk+
  905 eriol     20   0  368392   7636   6780 S   0,0  0,2   0:00.00 gvfs-afc-v+
  927 eriol     20   0  400772  32988  27052 S   0,0  0,8   0:00.12 xpad
  930 eriol     20   0  268928   5512   4808 S   0,0  0,1   0:00.01 gvfs-mtp-v+
  940 eriol     20   0  207964   7660   6904 S   0,0  0,2   0:00.00 menu-cached
  944 eriol     20   0  426456  22912  18576 S   0,0  0,6   0:00.05 light-lock+
  947 eriol     20   0  281560   6072   5240 S   0,0  0,2   0:00.00 gvfs-gphot+
  951 eriol     20   0  267000   6044   5440 S   0,0  0,2   0:00.00 gvfs-goa-v+
  957 eriol     20   0  187776   5168   4536 S   0,0  0,1   0:00.00 dconf-serv+
  974 eriol     20   0  376748  10040   8752 S   0,0  0,3   0:00.02 gvfsd-trash
 1000 eriol     20   0  888624  11552   8476 S   0,0  0,3   0:00.27 pulseaudio
 1025 eriol     20   0  780640  15368  13156 S   0,0  0,4   0:00.03 indicator-+
 1027 eriol     20   0  443076   8544   7456 S   0,0  0,2   0:00.02 indicator-+
 1059 eriol     20   0  519708  26420  21556 S   0,0  0,7   0:00.32 lxterminal
 1060 eriol     20   0   14980   1992   1832 S   0,0  0,0   0:00.00 gnome-pty-+
 1061 eriol     20   0   22984   5620   3624 S   0,0  0,1   0:00.03 bash
 2111 eriol     20   0 1515844 269060 131576 S   0,0  6,7   0:30.39 chrome
 2116 eriol     20   0    7556    716    644 S   0,0  0,0   0:00.00 cat
 2117 eriol     20   0    7556    720    648 S   0,0  0,0   0:00.00 cat
 2120 eriol     20   0  434104  53912  44032 S   0,0  1,3   0:00.16 chrome
 2121 eriol     20   0  121452   7888   6688 S   0,0  0,2   0:00.00 nacl_helper
 2124 eriol     20   0  434104  12528   2640 S   0,0  0,3   0:00.02 chrome
 2802 eriol     20   0 1321072 189268  56344 S   0,0  4,7   0:08.31 chrome
 2831 eriol     20   0  475348  66960  42680 S   0,0  1,7   0:00.09 chrome
 2833 eriol     20   0  402264  12176   2508 S   0,0  0,3   0:00.00 chrome
 2857 eriol     20   0 1996328 302272  93496 S   0,0  7,5   0:18.90 chrome
 2894 root      20   0       0      0      0 S   0,0  0,0   0:00.07 kworker/0:3
 2927 eriol     20   0 1237708 145656  75808 S   0,0  3,6   0:03.05 chrome
 2958 eriol     20   0  210628   6172   5024 S   0,0  0,2   0:00.00 oosplash
 2975 eriol     20   0  907264 152792 101368 S   0,0  3,8   0:01.11 soffice.bin
 3015 eriol     20   0 1300988 207236 105772 S   0,0  5,2   0:08.44 chrome
 3538 root      20   0       0      0      0 S   0,0  0,0   0:00.03 kworker/1:2
 3542 eriol     20   0 1178940 119540  74108 S   0,0  3,0   0:04.41 chrome
 3589 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kworker/u8+
 3593 eriol     20   0   12824   3312   2992 S   0,0  0,1   0:00.00 monitoring+
```


```
inxi -Fxz
```


```
System:    Host: pcchio Kernel: 4.13.0-17-generic x86_64 bits: 64 gcc: 7.2.0
           Desktop: LXDE (Openbox 3.6.1) Distro: Ubuntu 17.10
Machine:   Device: laptop System: Hewlett-Packard product: HP Pavilion dv6 Notebook PC v: Rev 1 serial: N/A
           Mobo: Hewlett-Packard model: 3628 v: 18.51 serial: N/A
           BIOS: Hewlett-Packard v: F.46 date: 08/25/2011
CPU:       Dual core Intel Core2 Duo T9550 (-MCP-)
           arch: Penryn rev.10 cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 10640
           clock speeds: max: 2667 MHz 1: 2660 MHz 2: 2660 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] RV730/M96 [Mobility Radeon HD 4650/5165]
           bus-ID: 01:00.0
           Display Server: x11 (X.Org 1.19.5 )
           drivers: ati,radeon (unloaded: modesetting,fbdev,vesa)
           Resolution: 1366x768@59.97hz
           OpenGL: renderer: AMD RV730 (DRM 2.50.0 / 4.13.0-17-generic, LLVM 5.0.0)
           version: 3.3 Mesa 17.2.2 Direct Render: Yes
Audio:     Card-1 Advanced Micro Devices [AMD/ATI] RV710/730 HDMI Audio [Radeon HD 4000 series]
           driver: snd_hda_intel bus-ID: 01:00.1
           Card-2 Intel 82801I (ICH9 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.13.0-17-generic
Network:   Card-1: Intel PRO/Wireless 5100 AGN [Shiloh] Network Connection
           driver: iwlwifi bus-ID: 02:00.0
           IF: wlp2s0 state: up mac: <filter>
           Card-2: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: 5000 bus-ID: 03:00.0
           IF: enp3s0 state: down mac: <filter>
Drives:    HDD Total Size: 500.1GB (15.1% used)
           ID-1: /dev/sda model: TOSHIBA_MK5055GS size: 500.1GB
Partition: ID-1: / size: 450G used: 63G (15%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 8.66GB used: 0.00GB (0%)
           fs: swap dev: /dev/sda2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 70.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 159 Uptime: 7 min Memory: 1034.7/3916.0MB
           Init: systemd runlevel: 5 Gcc sys: 7.2.0
           Client: Shell (monitoring.sh) inxi: 2.3.37
```

It seems like that the more I use the netbook, the less it goes slow...

---

### Post by vasa1 on 2017-11-30
You don't need to post *inxi -Fxz* each time. Just to give CPU information,```
inxi -Cxx
```will do.

And just to be clear, I didn't suggest turning off your adblocker. I think making it **stricter**, where possible, would help.

---

### Post by ancienthero on 2017-11-30
> **vasa1 said:**
> You don't need to post *inxi -Fxz* each time. Just to give CPU information,```
inxi -Cxx
```will do.

And just to be clear, I didn't suggest turning off your adblocker. I think making it **stricter**, where possible, would help.


Ok, I will update you tomorrow, as now I am back home and I use that notebook at work. Thank you for your advices :)

---

### Post by ancienthero on 2017-12-06
I have been waiting for a while before posting once again, because things seems to go a bit better after disabling hardware acceleration and making AdBlock stricter, but the problem is still here. 


```
top -n1 -o %MEM
```


```
top - 12:22:17 up 49 min,  1 user,  load average: 2,25, 2,03, 2,22
Tasks: 156 total,   2 running, 154 sleeping,   0 stopped,   0 zombie
%Cpu(s): 12,6 us,  2,9 sy,  0,1 ni, 54,7 id, 29,7 wa,  0,0 hi,  0,0 si,  0,0 st
KiB Mem :  4009960 total,  1075664 free,  1079508 used,  1854788 buff/cache
KiB Swap:  8454140 total,  8454140 free,        0 used.  2583616 avail Mem 


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 1133 eriol     20   0 1662964 306816 145136 S   6,7  7,7   2:59.83 chrome
 1491 eriol     20   0 1954256 290584  78372 S   0,0  7,2   0:31.07 chrome
 2480 eriol     20   0 1865236 240708 117148 S   0,0  6,0   0:18.27 chrome
 1260 eriol     20   0 1344080 206968  55648 S   0,0  5,2   0:21.58 chrome
 4759 eriol     20   0 1006704 186632 107264 S   6,7  4,7   0:01.74 soffice.bin
 3598 eriol     20   0 1228992 145728  79052 S   0,0  3,6   0:06.80 chrome
 1301 eriol     20   0  580212  76312  45944 S   0,0  1,9   0:01.43 chrome
  620 root      20   0  581524  58448  41588 R  13,3  1,5   1:06.38 Xorg
 1145 eriol     20   0  434104  53972  44084 S   0,0  1,3   0:00.16 chrome
  932 eriol     20   0  825508  36784  27792 S   6,7  0,9   0:02.20 pcmanfm
  939 eriol     20   0  739336  36576  29792 S   0,0  0,9   0:00.80 nm-applet
  983 eriol     20   0  400740  32644  26708 S   0,0  0,8   0:00.16 xpad
  929 eriol     20   0 1037792  32076  24276 S   0,0  0,8   0:03.26 lxpanel
 3375 eriol     20   0  519496  26588  21724 S   0,0  0,7   0:00.22 lxterminal
 1042 eriol     20   0  427732  25228  20676 S   0,0  0,6   0:00.13 light-lock+
  954 eriol     20   0  592976  24672  20028 S   0,0  0,6   0:00.17 update-not+
  940 eriol     20   0  382020  22020  18116 S   0,0  0,5   0:00.08 xfce4-powe+
  925 eriol     20   0  393644  21452  16804 S   0,0  0,5   0:00.62 openbox
  518 root      20   0  488532  18248  15024 S   0,0  0,5   0:00.76 NetworkMan+
  845 eriol     20   0  371996  15892  13860 S   0,0  0,4   0:00.12 lxsession
  522 root      20   0  468104  15804   9768 S   0,0  0,4   0:00.03 snapd
  626 colord    20   0  332336  15448  10324 S   0,0  0,4   0:00.14 colord
 1052 eriol     20   0  780640  15420  13208 S   0,0  0,4   0:00.06 indicator-+
  649 whoopsie  20   0  461472  12884  11020 S   0,0  0,3   0:00.10 whoopsie
 1149 eriol     20   0  434104  12592   2700 S   0,0  0,3   0:00.08 chrome
 1303 eriol     20   0  402232  12060   2428 S   0,0  0,3   0:00.00 chrome
  532 root      20   0  312040  11748   8540 S   0,0  0,3   0:00.28 polkitd
 1091 eriol     20   0  888628  11664   8568 S   0,0  0,3   0:04.05 pulseaudio
  934 eriol     20   0  297296  11268   9972 S   0,0  0,3   0:00.01 lxpolkit
  501 root      20   0  463812  10708   8220 S   0,0  0,3   0:00.49 udisksd
  976 eriol     20   0  312780  10568   9044 S   0,0  0,3   0:00.03 gvfs-udisk+
  933 eriol     20   0  164488  10068   8828 S   0,0  0,3   0:00.00 xfce4-powe+
 1093 eriol     20   0  376748   9832   8540 S   0,0  0,2   0:00.02 gvfsd-trash
 1844 root      20   0  102828   9532   7052 S   0,0  0,2   0:00.04 cupsd
  516 root      20   0  427556   9472   7600 S   0,0  0,2   0:00.04 ModemManag+
 2106 eriol     20   0  376840   9440   8352 S   0,0  0,2   0:00.01 gvfsd-netw+
  971 root      20   0  312088   8936   7544 S   0,0  0,2   0:00.22 upowerd
  610 root      20   0  308368   8884   7648 S   0,0  0,2   0:00.03 lightdm
  513 root      20   0  301232   8868   7844 S   0,0  0,2   0:00.07 accounts-d+
 2184 eriol     20   0  281344   8624   7684 S   0,0  0,2   0:00.02 gnome-keyr+
    1 root      20   0  154536   8488   6460 S   0,0  0,2   0:02.07 systemd
 1054 eriol     20   0  443076   8476   7396 S   0,0  0,2   0:00.14 indicator-+
 1146 eriol     20   0  121452   7856   6660 S   0,0  0,2   0:00.00 nacl_helper
  839 eriol     20   0   80348   7780   6520 S   0,0  0,2   0:00.05 systemd
  914 eriol     20   0  431604   7748   6880 S   0,0  0,2   0:00.00 gvfsd-fuse
  978 eriol     20   0  207964   7580   6824 S   0,0  0,2   0:00.00 menu-cached
 1040 eriol     20   0  368392   7564   6704 S   0,0  0,2   0:00.00 gvfs-afc-v+
 2162 eriol     20   0  374180   7532   6612 S   0,0  0,2   0:00.01 gvfsd-dnssd
  909 eriol     20   0  284864   7140   6180 S   0,0  0,2   0:00.03 gvfsd
  720 root      20   0  245964   6956   6064 S   0,0  0,2   0:00.02 lightdm
  632 root      20   0   48836   6696   6020 S   0,0  0,2   0:00.09 wpa_suppli+
  248 root      20   0   62152   6632   5912 S   0,0  0,2   0:00.36 systemd-jo+
  592 systemd+  20   0   66208   6480   5260 S   0,0  0,2   0:00.73 systemd-re+
 4742 eriol     20   0  145092   6248   5100 S   0,0  0,2   0:00.00 oosplash
  526 root      20   0   65672   5944   5192 S   0,0  0,1   0:00.08 systemd-lo+
 1074 eriol     20   0  281560   5864   5052 S   0,0  0,1   0:00.00 gvfs-gphot+
 1082 eriol     20   0  267000   5844   5240 S   0,0  0,1   0:00.00 gvfs-goa-v+
 3377 eriol     20   0   23080   5784   3688 S   0,0  0,1   0:00.06 bash
  622 root      20   0   72136   5780   5048 S   0,0  0,1   0:00.02 sshd
  261 root      20   0   47044   5708   3048 S   0,0  0,1   0:01.11 systemd-ud+
 1048 eriol     20   0  268928   5400   4704 S   0,0  0,1   0:00.00 gvfs-mtp-v+
 1066 eriol     20   0  187776   5196   4532 S   0,0  0,1   0:00.00 dconf-serv+
  952 eriol     20   0   58932   5052   4540 S   0,0  0,1   0:00.00 xfconfd
  305 systemd+  20   0  145312   5036   4468 S   0,0  0,1   0:00.04 systemd-ti+
  507 message+  20   0   48352   4916   3608 S   0,0  0,1   0:00.53 dbus-daemon
  861 eriol     20   0   47912   4684   3728 S   0,0  0,1   0:00.18 dbus-daemon
 3140 root      20   0   16228   3884   3020 S   0,0  0,1   0:00.00 dhclient
  525 syslog    20   0  256536   3840   2896 S   0,0  0,1   0:00.04 rsyslogd
  498 avahi     20   0   49456   3784   3376 S   0,0  0,1   0:00.05 avahi-daem+
 5096 eriol     20   0   46360   3728   3208 R   0,0  0,1   0:00.01 top
  506 root      20   0   38564   3516   3160 S   0,0  0,1   0:00.11 irqbalance
 3676 eriol     20   0   12884   3228   2852 S   0,0  0,1   0:00.04 monitoring+
  523 root      20   0   31244   3116   2828 S   0,0  0,1   0:00.00 cron
  659 kernoops  20   0   56744   2752   2312 S   0,0  0,1   0:00.05 kerneloops
  840 eriol     20   0  186128   2144     56 S   0,0  0,1   0:00.00 (sd-pam)
 3376 eriol     20   0   14980   1908   1748 S   0,0  0,0   0:00.00 gnome-pty-+
  607 root      20   0   16124   1872   1736 S   0,0  0,0   0:00.00 agetty
  504 root      20   0    4500    920    852 S   0,0  0,0   0:00.09 acpid
 1139 eriol     20   0    7556    824    756 S   0,0  0,0   0:00.00 cat
 1138 eriol     20   0    7556    776    704 S   0,0  0,0   0:00.00 cat
  505 avahi     20   0   49332    360      0 S   0,0  0,0   0:00.00 avahi-daem+
  898 eriol     20   0   11228    320      0 S   0,0  0,0   0:00.00 ssh-agent
  947 eriol     20   0   11228    320      0 S   0,0  0,0   0:00.00 ssh-agent
    2 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kthreadd
    4 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/0:+
    6 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 mm_percpu_+
    7 root      20   0       0      0      0 S   0,0  0,0   0:00.06 ksoftirqd/0
    8 root      20   0       0      0      0 S   0,0  0,0   0:00.94 rcu_sched
    9 root      20   0       0      0      0 S   0,0  0,0   0:00.00 rcu_bh
   10 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 migration/0
   11 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 watchdog/0
   12 root      20   0       0      0      0 S   0,0  0,0   0:00.00 cpuhp/0
   13 root      20   0       0      0      0 S   0,0  0,0   0:00.00 cpuhp/1
   14 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 watchdog/1
   15 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 migration/1
   16 root      20   0       0      0      0 S   0,0  0,0   0:00.06 ksoftirqd/1
   18 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/1:+
   19 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kdevtmpfs
   20 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 netns
   23 root      20   0       0      0      0 S   0,0  0,0   0:00.00 khungtaskd
   24 root      20   0       0      0      0 S   0,0  0,0   0:00.00 oom_reaper
   25 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 writeback
   26 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kcompactd0
   27 root      25   5       0      0      0 S   0,0  0,0   0:00.00 ksmd
   28 root      39  19       0      0      0 S   0,0  0,0   0:00.00 khugepaged
   29 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 crypto
   30 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kintegrityd
   31 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kblockd
   32 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 ata_sff
   33 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 md
   34 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 edac-poller
   35 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 devfreq_wq
   36 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 watchdogd
   38 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kauditd
   39 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kswapd0
   40 root      20   0       0      0      0 S   0,0  0,0   0:00.00 ecryptfs-k+
   82 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kthrotld
   83 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 acpi_therm+
   93 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 ipv6_addrc+
  118 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 charger_ma+
  168 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 firewire
  170 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 firewire_o+
  171 root     -51   0       0      0      0 S   0,0  0,0   0:00.00 irq/16-mmc0
  172 root      20   0       0      0      0 S   0,0  0,0   0:00.02 scsi_eh_0
  173 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 scsi_tmf_0
  174 root      20   0       0      0      0 S   0,0  0,0   0:00.00 scsi_eh_1
  175 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 scsi_tmf_1
  176 root      20   0       0      0      0 S   0,0  0,0   0:00.00 scsi_eh_2
  177 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 scsi_tmf_2
  178 root      20   0       0      0      0 S   0,0  0,0   0:00.00 scsi_eh_3
  179 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 scsi_tmf_3
  180 root      20   0       0      0      0 S   0,0  0,0   0:00.00 scsi_eh_4
  181 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 scsi_tmf_4
  182 root      20   0       0      0      0 S   0,0  0,0   0:00.00 scsi_eh_5
  183 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 scsi_tmf_5
  185 root      20   0       0      0      0 S   0,0  0,0   0:00.30 kworker/u8+
  186 root      20   0       0      0      0 S   0,0  0,0   0:00.32 kworker/u8+
  189 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 ttm_swap
  194 root       0 -20       0      0      0 S   0,0  0,0   0:00.34 kworker/1:+
  195 root       0 -20       0      0      0 S   0,0  0,0   0:00.01 kworker/0:+
  215 root      20   0       0      0      0 S   0,0  0,0   0:00.45 jbd2/sda1-8
  216 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 ext4-rsv-c+
  303 root      20   0       0      0      0 S   0,0  0,0   0:00.00 rc0
  313 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kmemstick
  314 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 cfg80211
  322 root     -51   0       0      0      0 S   0,0  0,0   0:03.70 irq/33-iwl+
  323 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/u9+
  627 root       0 -20       0      0      0 S   0,0  0,0   0:00.06 kworker/u9+
 2442 root      20   0       0      0      0 S   0,0  0,0   0:00.55 kworker/1:0
 2719 root      20   0       0      0      0 S   0,0  0,0   0:00.34 kworker/0:1
 3160 root      20   0       0      0      0 S   0,0  0,0   0:00.06 kworker/u8+
 3257 root      20   0       0      0      0 S   0,0  0,0   0:00.31 kworker/1:2
 3261 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kworker/0:0
 3563 root      20   0       0      0      0 S   0,0  0,0   0:00.01 kworker/1:1
 3610 root      20   0       0      0      0 S   0,0  0,0   0:00.01 kworker/u8+
 4051 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kworker/0:2
```


```
top -n1 -o %CPU
```


```
top - 12:22:17 up 49 min,  1 user,  load average: 2,25, 2,03, 2,22
Tasks: 156 total,   1 running, 155 sleeping,   0 stopped,   0 zombie
%Cpu(s): 12,6 us,  2,9 sy,  0,1 ni, 54,7 id, 29,7 wa,  0,0 hi,  0,0 si,  0,0 st
KiB Mem :  4009960 total,  1075888 free,  1079284 used,  1854788 buff/cache
KiB Swap:  8454140 total,  8454140 free,        0 used.  2583840 avail Mem 


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 5099 eriol     20   0   46360   3868   3352 R   6,2  0,1   0:00.01 top
    1 root      20   0  154536   8488   6460 S   0,0  0,2   0:02.07 systemd
    2 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kthreadd
    4 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/0:+
    6 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 mm_percpu_+
    7 root      20   0       0      0      0 S   0,0  0,0   0:00.06 ksoftirqd/0
    8 root      20   0       0      0      0 S   0,0  0,0   0:00.94 rcu_sched
    9 root      20   0       0      0      0 S   0,0  0,0   0:00.00 rcu_bh
   10 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 migration/0
   11 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 watchdog/0
   12 root      20   0       0      0      0 S   0,0  0,0   0:00.00 cpuhp/0
   13 root      20   0       0      0      0 S   0,0  0,0   0:00.00 cpuhp/1
   14 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 watchdog/1
   15 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 migration/1
   16 root      20   0       0      0      0 S   0,0  0,0   0:00.06 ksoftirqd/1
   18 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/1:+
   19 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kdevtmpfs
   20 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 netns
   23 root      20   0       0      0      0 S   0,0  0,0   0:00.00 khungtaskd
   24 root      20   0       0      0      0 S   0,0  0,0   0:00.00 oom_reaper
   25 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 writeback
   26 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kcompactd0
   27 root      25   5       0      0      0 S   0,0  0,0   0:00.00 ksmd
   28 root      39  19       0      0      0 S   0,0  0,0   0:00.00 khugepaged
   29 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 crypto
   30 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kintegrityd
   31 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kblockd
   32 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 ata_sff
   33 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 md
   34 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 edac-poller
   35 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 devfreq_wq
   36 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 watchdogd
   38 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kauditd
   39 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kswapd0
   40 root      20   0       0      0      0 S   0,0  0,0   0:00.00 ecryptfs-k+
   82 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kthrotld
   83 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 acpi_therm+
   93 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 ipv6_addrc+
  118 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 charger_ma+
  168 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 firewire
  170 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 firewire_o+
  171 root     -51   0       0      0      0 S   0,0  0,0   0:00.00 irq/16-mmc0
  172 root      20   0       0      0      0 S   0,0  0,0   0:00.02 scsi_eh_0
  173 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 scsi_tmf_0
  174 root      20   0       0      0      0 S   0,0  0,0   0:00.00 scsi_eh_1
  175 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 scsi_tmf_1
  176 root      20   0       0      0      0 S   0,0  0,0   0:00.00 scsi_eh_2
  177 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 scsi_tmf_2
  178 root      20   0       0      0      0 S   0,0  0,0   0:00.00 scsi_eh_3
  179 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 scsi_tmf_3
  180 root      20   0       0      0      0 S   0,0  0,0   0:00.00 scsi_eh_4
  181 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 scsi_tmf_4
  182 root      20   0       0      0      0 S   0,0  0,0   0:00.00 scsi_eh_5
  183 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 scsi_tmf_5
  185 root      20   0       0      0      0 S   0,0  0,0   0:00.30 kworker/u8+
  186 root      20   0       0      0      0 S   0,0  0,0   0:00.32 kworker/u8+
  189 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 ttm_swap
  194 root       0 -20       0      0      0 S   0,0  0,0   0:00.34 kworker/1:+
  195 root       0 -20       0      0      0 S   0,0  0,0   0:00.01 kworker/0:+
  215 root      20   0       0      0      0 S   0,0  0,0   0:00.45 jbd2/sda1-8
  216 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 ext4-rsv-c+
  248 root      20   0   62152   6632   5912 S   0,0  0,2   0:00.36 systemd-jo+
  261 root      20   0   47044   5708   3048 S   0,0  0,1   0:01.11 systemd-ud+
  303 root      20   0       0      0      0 S   0,0  0,0   0:00.00 rc0
  305 systemd+  20   0  145312   5036   4468 S   0,0  0,1   0:00.04 systemd-ti+
  313 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kmemstick
  314 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 cfg80211
  322 root     -51   0       0      0      0 S   0,0  0,0   0:03.70 irq/33-iwl+
  323 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/u9+
  498 avahi     20   0   49456   3784   3376 S   0,0  0,1   0:00.05 avahi-daem+
  501 root      20   0  463812  10708   8220 S   0,0  0,3   0:00.49 udisksd
  504 root      20   0    4500    920    852 S   0,0  0,0   0:00.09 acpid
  505 avahi     20   0   49332    360      0 S   0,0  0,0   0:00.00 avahi-daem+
  506 root      20   0   38564   3516   3160 S   0,0  0,1   0:00.11 irqbalance
  507 message+  20   0   48352   4916   3608 S   0,0  0,1   0:00.53 dbus-daemon
  513 root      20   0  301232   8868   7844 S   0,0  0,2   0:00.07 accounts-d+
  516 root      20   0  427556   9472   7600 S   0,0  0,2   0:00.04 ModemManag+
  518 root      20   0  488532  18248  15024 S   0,0  0,5   0:00.76 NetworkMan+
  522 root      20   0  468104  15804   9768 S   0,0  0,4   0:00.03 snapd
  523 root      20   0   31244   3116   2828 S   0,0  0,1   0:00.00 cron
  525 syslog    20   0  256536   3840   2896 S   0,0  0,1   0:00.04 rsyslogd
  526 root      20   0   65672   5944   5192 S   0,0  0,1   0:00.08 systemd-lo+
  532 root      20   0  312040  11748   8540 S   0,0  0,3   0:00.28 polkitd
  592 systemd+  20   0   66208   6480   5260 S   0,0  0,2   0:00.73 systemd-re+
  607 root      20   0   16124   1872   1736 S   0,0  0,0   0:00.00 agetty
  610 root      20   0  308368   8884   7648 S   0,0  0,2   0:00.03 lightdm
  620 root      20   0  581524  58448  41588 S   0,0  1,5   1:06.39 Xorg
  622 root      20   0   72136   5780   5048 S   0,0  0,1   0:00.02 sshd
  626 colord    20   0  332336  15448  10324 S   0,0  0,4   0:00.14 colord
  627 root       0 -20       0      0      0 S   0,0  0,0   0:00.06 kworker/u9+
  632 root      20   0   48836   6696   6020 S   0,0  0,2   0:00.09 wpa_suppli+
  649 whoopsie  20   0  461472  12884  11020 S   0,0  0,3   0:00.10 whoopsie
  659 kernoops  20   0   56744   2752   2312 S   0,0  0,1   0:00.05 kerneloops
  720 root      20   0  245964   6956   6064 S   0,0  0,2   0:00.02 lightdm
  839 eriol     20   0   80348   7780   6520 S   0,0  0,2   0:00.05 systemd
  840 eriol     20   0  186128   2144     56 S   0,0  0,1   0:00.00 (sd-pam)
  845 eriol     20   0  371996  15892  13860 S   0,0  0,4   0:00.12 lxsession
  861 eriol     20   0   47912   4684   3728 S   0,0  0,1   0:00.18 dbus-daemon
  898 eriol     20   0   11228    320      0 S   0,0  0,0   0:00.00 ssh-agent
  909 eriol     20   0  284864   7140   6180 S   0,0  0,2   0:00.03 gvfsd
  914 eriol     20   0  431604   7748   6880 S   0,0  0,2   0:00.00 gvfsd-fuse
  925 eriol     20   0  393644  21452  16804 S   0,0  0,5   0:00.62 openbox
  929 eriol     20   0 1037792  32076  24276 S   0,0  0,8   0:03.26 lxpanel
  932 eriol     20   0  825508  36784  27792 S   0,0  0,9   0:02.20 pcmanfm
  933 eriol     20   0  164488  10068   8828 S   0,0  0,3   0:00.00 xfce4-powe+
  934 eriol     20   0  297296  11268   9972 S   0,0  0,3   0:00.01 lxpolkit
  939 eriol     20   0  739336  36576  29792 S   0,0  0,9   0:00.80 nm-applet
  940 eriol     20   0  382020  22020  18116 S   0,0  0,5   0:00.08 xfce4-powe+
  947 eriol     20   0   11228    320      0 S   0,0  0,0   0:00.00 ssh-agent
  952 eriol     20   0   58932   5052   4540 S   0,0  0,1   0:00.00 xfconfd
  954 eriol     20   0  592976  24672  20028 S   0,0  0,6   0:00.17 update-not+
  971 root      20   0  312088   8936   7544 S   0,0  0,2   0:00.22 upowerd
  976 eriol     20   0  312780  10568   9044 S   0,0  0,3   0:00.03 gvfs-udisk+
  978 eriol     20   0  207964   7580   6824 S   0,0  0,2   0:00.00 menu-cached
  983 eriol     20   0  400740  32644  26708 S   0,0  0,8   0:00.16 xpad
 1040 eriol     20   0  368392   7564   6704 S   0,0  0,2   0:00.00 gvfs-afc-v+
 1042 eriol     20   0  427732  25228  20676 S   0,0  0,6   0:00.13 light-lock+
 1048 eriol     20   0  268928   5400   4704 S   0,0  0,1   0:00.00 gvfs-mtp-v+
 1052 eriol     20   0  780640  15420  13208 S   0,0  0,4   0:00.06 indicator-+
 1054 eriol     20   0  443076   8476   7396 S   0,0  0,2   0:00.14 indicator-+
 1066 eriol     20   0  187776   5196   4532 S   0,0  0,1   0:00.00 dconf-serv+
 1074 eriol     20   0  281560   5864   5052 S   0,0  0,1   0:00.00 gvfs-gphot+
 1082 eriol     20   0  267000   5844   5240 S   0,0  0,1   0:00.00 gvfs-goa-v+
 1091 eriol     20   0  888628  11664   8568 S   0,0  0,3   0:04.05 pulseaudio
 1093 eriol     20   0  376748   9832   8540 S   0,0  0,2   0:00.02 gvfsd-trash
 1133 eriol     20   0 1662964 306816 145136 S   0,0  7,7   2:59.83 chrome
 1138 eriol     20   0    7556    776    704 S   0,0  0,0   0:00.00 cat
 1139 eriol     20   0    7556    824    756 S   0,0  0,0   0:00.00 cat
 1145 eriol     20   0  434104  53972  44084 S   0,0  1,3   0:00.16 chrome
 1146 eriol     20   0  121452   7856   6660 S   0,0  0,2   0:00.00 nacl_helper
 1149 eriol     20   0  434104  12592   2700 S   0,0  0,3   0:00.08 chrome
 1260 eriol     20   0 1344080 206968  55648 S   0,0  5,2   0:21.58 chrome
 1301 eriol     20   0  580212  76312  45944 S   0,0  1,9   0:01.43 chrome
 1303 eriol     20   0  402232  12060   2428 S   0,0  0,3   0:00.00 chrome
 1491 eriol     20   0 1954256 290584  78372 S   0,0  7,2   0:31.07 chrome
 1844 root      20   0  102828   9532   7052 S   0,0  0,2   0:00.04 cupsd
 2106 eriol     20   0  376840   9440   8352 S   0,0  0,2   0:00.01 gvfsd-netw+
 2162 eriol     20   0  374180   7532   6612 S   0,0  0,2   0:00.01 gvfsd-dnssd
 2184 eriol     20   0  281344   8624   7684 S   0,0  0,2   0:00.02 gnome-keyr+
 2442 root      20   0       0      0      0 S   0,0  0,0   0:00.55 kworker/1:0
 2480 eriol     20   0 1865236 240708 117148 S   0,0  6,0   0:18.27 chrome
 2719 root      20   0       0      0      0 S   0,0  0,0   0:00.34 kworker/0:1
 3140 root      20   0   16228   3884   3020 S   0,0  0,1   0:00.00 dhclient
 3160 root      20   0       0      0      0 S   0,0  0,0   0:00.06 kworker/u8+
 3257 root      20   0       0      0      0 S   0,0  0,0   0:00.31 kworker/1:2
 3261 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kworker/0:0
 3375 eriol     20   0  519496  26588  21724 S   0,0  0,7   0:00.22 lxterminal
 3376 eriol     20   0   14980   1908   1748 S   0,0  0,0   0:00.00 gnome-pty-+
 3377 eriol     20   0   23080   5784   3688 S   0,0  0,1   0:00.06 bash
 3563 root      20   0       0      0      0 S   0,0  0,0   0:00.01 kworker/1:1
 3598 eriol     20   0 1228992 145728  79052 S   0,0  3,6   0:06.80 chrome
 3610 root      20   0       0      0      0 S   0,0  0,0   0:00.01 kworker/u8+
 3676 eriol     20   0   12884   3228   2852 S   0,0  0,1   0:00.04 monitoring+
 4051 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kworker/0:2
 4742 eriol     20   0  145092   6248   5100 S   0,0  0,2   0:00.00 oosplash
 4759 eriol     20   0 1006704 186632 107264 S   0,0  4,7   0:01.74 soffice.bin
```


```
inxi -Cxx
```


```
CPU:       Dual core Intel Core2 Duo T9550 (-MCP-)
           arch: Penryn rev.10 cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 10640
           clock speeds: min/max: 800/2667 MHz 1: 2660 MHz 2: 2660 MHz
```

Anyway I have found that values given by inxi (MHz 1: 2660 MHz 2: 2660 MHz) are always the same, just after booting

---

### Post by vasa1 on 2017-12-06
What Chrome extensions do you have?

---

### Post by ancienthero on 2017-12-06
> **vasa1 said:**
> What Chrome extensions do you have?

Except AdBlock, there are only the default ones. Google Documents, etc...

---

### Post by vasa1 on 2017-12-06
Google Docs can be quite resource-demanding.

---

### Post by ancienthero on 2017-12-06
Disabled everything. Will see what happens and let you know

---

### Post by ancienthero on 2018-03-17
The problem was the hard disk. I replaced it with an ssd and now my PC is reborn. Thank you for your help, anyway :)

---

