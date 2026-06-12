---
title: "Shouldn't Ubuntu be faster than Windows XP?"
date: 2008-04-17
forum: Desktop Environments
---

### Post by ak87 on 2008-04-17
Hi!

I've succesfully installed Ubuntu 7.10 on my laptop (hp dv6544eo) and everything seemed to work great... I even got the message that there was some drivers (graphics and wireless) that needed to be activated, so i did that. 

I used Windows XP on the same laptop, before I installed Ubuntu... And it seems that Ubuntu is much slower than XP. 

When I browse through programs in the top menue... It kind of lags, doen't update my selection in "real time", the same goes for all the other programs, like firefox and so on. Even when I close and open windows, I experience some kind of delay.
When I scroll through webpages, it's the most anoying, it lags like hell... and don't start me on flashvideos :(

I thought it was something with the graphic effects (compiz), so i diabled it... But it didn't help

What can I do? Is there something wrong with my setup? Is my grahic card not propertly installed/configured?

Plz help

My specs:
AMD Turion X2 1.8GHz
2 GB Ram
Nvidia Geforce 8400 GS
6 GB in Swap and 50 GB in root

//Alex

---

### Post by aysiu on 2008-04-17
It's very possible your graphics card isn't configured properly.

With the processor and RAM you have, there's no reason for any kind of lag (I have no idea why your swap partition is so huge, though!).

Have you tried [enabling the Nvidia driver for your card?](http://www.psychocats.net/ubuntu/nvidia)

---

### Post by kirsis on 2008-04-17
With those specs, I'd say there's definitely something wrong with your set up.

It could be the drivers. I wouldn't know, I've never had an ATI/nVidia card (and Intel always works just right for me) but it seems like a common problem all around.

Also, with a 2x turion I don't think it should be an issue, but on my old *** laptop I found that certain GTK and icon themes brought the speed down quite noticably. Try a simple theme that doesn't use vectors and/or another icon set (though, again, this doesnt not seem like it should be an issue on most modern computers).

And finally may I suggest you try KDE (if you're currently a gnome user). KDE uses a different GUI toolkit (Qt), which does not have the same redraw latency that GTK+ does. I remember that it was quite weird for me too, coming from windows, to get used to it. I tried KDE for a while and though I didn't stick with it, the UI felt a lot smoother.

---

### Post by ak87 on 2008-04-17
> **aysiu said:**
> It's very possible your graphics card isn't configured properly.

With the processor and RAM you have, there's no reason for any kind of lag (I have no idea why your swap partition is so huge, though!).

Have you tried [enabling the Nvidia driver for your card?](http://www.psychocats.net/ubuntu/nvidia)

This was the first thing I did... It asked me right away when I started Ubuntu for the first time

I'll try KDE right away....

---

### Post by bingoUV on 2008-04-17
Could you post the output of 
```

glxinfo | grep -i direct

```

---

### Post by ak87 on 2008-04-17
> **bingoUV said:**
> Could you post the output of 
```

glxinfo | grep -i direct

```

Output:
direct rendering: yes

I noticed that KDE runs muck faster than GNOME... but still flashvideos lags a lot
I would prefer GNOME... hope there is fix for this problem

---

### Post by alejo0823 on 2008-04-17
try running the command

> top


also it may be the tracker eating your CPU try disable it.

---

### Post by Steveway on 2008-04-17
The first thing that caught my eye was your swap-partition.
6GB is far to much, unless you do some pro-studio like video-editing or so.
While 2,5x the amount of RAM as swap is recommended I would recommend either 2,5GB if you want to use suspend-to-ram or to-disk. Or about 1GB if you don't need that.

---

### Post by bdstein on 2008-04-17
Yea I think that is way to much swap as well.  I have always been told that swap should = ram or even as much as 2XRAM but not more.

---

### Post by bilijoe on 2008-04-17
> **bingoUV said:**
> Could you post the output of 
```

glxinfo | grep -i direct

```
After reading your post, I ran the above command, mostly out of curiosity, and got the following result
> direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
Don.t I want direct rendering?  and where is LIBGL_DEBUG?

---

### Post by russo.mic on 2008-04-18
May I vote for a video problem?  

I don't even use a swap, with 2 gigs of ram,  I don't see much of a reason to.  When I activate a swap file, I can see it NEVER get used in my resources.  I've always wondered if I'm setting it up wrong, but I never have any system lag, so have no reason to research further.

Russo.

---

### Post by ak87 on 2008-04-18
Ok.... I understand... I have too much in SWAP, but it cannot hurt, or can it?

The system is still slow, slower than Vista (run it on the same laptop) and much much slower than XP

---

### Post by ak87 on 2008-04-18
> **alejo0823 said:**
> try running the command



also it may be the tracker eating your CPU try disable it.

> ak87@ak87-laptop:~$ top

top - 12:37:32 up 4 min,  2 users,  load average: 1.68, 1.18, 0.52
Tasks: 114 total,   1 running, 113 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.0%us,  0.8%sy,  0.0%ni, 43.9%id,  0.0%wa, 26.0%hi, 25.2%si,  0.0%st
Mem:   2075360k total,   466832k used,  1608528k free,    11384k buffers
Swap:  5855652k total,        0k used,  5855652k free,   248788k cached
 Unknown command - try 'h' for help 
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
    7 root      35  19     0    0    0 S   59  0.0   1:55.33 ksoftirqd/1        
 5764 ak87      15   0 81568  20m  11m S   25  1.0   0:03.83 gnome-terminal     
 5649 ak87      15   0 46792  24m 9012 S    7  1.2   0:11.17 compiz.real        
 5334 root      15   0 55264  28m 7056 S    4  1.4   0:41.27 Xorg               
 5897 ak87      15   0  172m  44m  20m S    1  2.2   0:50.30 firefox-bin        
 5020 haldaemo  15   0  3260 1188 1036 S    0  0.1   0:00.03 hald-addon-stor    
 5785 ak87      15   0  2368 1156  876 R    0  0.1   0:00.69 top                
    1 root      15   0  2948 1852  532 S    0  0.1   0:01.38 init               
    2 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S    0  0.0   0:00.02 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      10  -5     0    0    0 S    0  0.0   0:00.16 events/0           
   10 root      10  -5     0    0    0 S    0  0.0   0:01.38 events/1           
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper 

This is the output...
What do you mean by "disabling tracker"?

---

### Post by kirsis on 2008-04-18
> **ak87 said:**
> Ok.... I understand... I have too much in SWAP, but it cannot hurt, or can it?

No, too much SWAP can't hurt. The unrequired portions are just unused, thus it's recommended not to overdo swap and put that space to use.



As for the tracker, it's an application that indexes filesw on your hard drive for fast search operations. It can slow down your system a lot, when running, but I don't see it among the top apps, so I'd guess it's not the issue. (though I'm no expert in cli task handling and such)

---

### Post by Tom Mann on 2008-04-18
I found top only shows one screenful of info (I haven't got the knack of the control keys yet)

A ```
ps -A
``` would be better here no?

---

### Post by ak87 on 2008-04-18
> **Tom Mann said:**
> I found top only shows one screenful of info (I haven't got the knack of the control keys yet)

A ```
ps -A
``` would be better here no?

Here is the output:

>  ak87@ak87-laptop:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:04:11 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 khelper
   31 ?        00:00:00 kblockd/0
   32 ?        00:00:00 kblockd/1
   33 ?        00:00:00 kacpid
   34 ?        00:00:00 kacpi_notify
  182 ?        00:00:00 kseriod
  210 ?        00:00:00 pdflush
  211 ?        00:00:00 pdflush
  212 ?        00:00:00 kswapd0
  263 ?        00:00:00 aio/0
  264 ?        00:00:00 aio/1
 2202 ?        00:00:00 ksuspend_usbd
 2203 ?        00:00:00 khubd
 2237 ?        00:00:00 khpsbpkt
 2250 ?        00:00:00 ata/0
 2251 ?        00:00:00 ata/1
 2252 ?        00:00:00 ata_aux
 2346 ?        00:00:00 scsi_eh_0
 2347 ?        00:00:00 scsi_eh_1
 2348 ?        00:00:00 scsi_eh_2
 2349 ?        00:00:00 scsi_eh_3
 2399 ?        00:00:00 knodemgrd_0
 2560 ?        00:00:00 kjournald
 2770 ?        00:00:00 udevd
 3732 ?        00:00:00 kmmcd
 3775 ?        00:00:00 kpsmoused
 4281 ?        00:00:00 mount.ntfs
 4516 tty4     00:00:00 getty
 4517 tty5     00:00:00 getty
 4519 tty2     00:00:00 getty
 4522 tty3     00:00:00 getty
 4523 tty1     00:00:00 getty
 4524 tty6     00:00:00 getty
 4735 ?        00:00:00 acpid
 4779 ?        00:00:00 kondemand/0
 4780 ?        00:00:00 kondemand/1
 4846 ?        00:00:00 syslogd
 4900 ?        00:00:00 dd
 4902 ?        00:00:00 klogd
 4923 ?        00:00:00 dbus-daemon
 4939 ?        00:00:00 NetworkManager
 4953 ?        00:00:00 NetworkManagerD
 4966 ?        00:00:00 system-tools-ba
 4967 ?        00:00:00 dbus-daemon
 4986 ?        00:00:00 hald
 4987 ?        00:00:00 hald-runner
 5045 ?        00:00:00 avahi-daemon
 5046 ?        00:00:00 avahi-daemon
 5064 ?        00:00:00 hald-addon-keyb
 5068 ?        00:00:00 hald-addon-keyb
 5069 ?        00:00:00 hald-addon-keyb
 5070 ?        00:00:00 hald-addon-keyb
 5074 ?        00:00:00 hald-addon-cpuf
 5076 ?        00:00:00 hald-addon-acpi
 5086 ?        00:00:00 hald-addon-stor
 5087 ?        00:00:00 cupsd
 5144 ?        00:00:00 dirmngr
 5229 ?        00:00:00 console-kit-dae
 5307 ?        00:00:00 dhcdbd
 5338 ?        00:00:00 hcid
 5350 ?        00:00:00 bluetoothd-serv
 5351 ?        00:00:00 bluetoothd-serv
 5360 ?        00:00:00 krfcommd
 5392 ?        00:00:00 gdm
 5395 ?        00:00:00 gdm
 5399 tty7     00:00:33 Xorg
 5441 ?        00:00:00 atd
 5455 ?        00:00:00 cron
 5583 ?        00:00:00 gnome-keyring-d
 5586 ?        00:00:00 x-session-manag
 5626 ?        00:00:00 ssh-agent
 5628 ?        00:00:00 gconfd-2
 5632 ?        00:00:00 dbus-daemon
 5634 ?        00:00:00 gnome-settings-
 5640 ?        00:00:00 compiz
 5642 ?        00:00:03 gnome-panel
 5644 ?        00:00:00 nautilus
 5651 ?        00:00:00 gnome-volume-ma
 5653 ?        00:00:00 bonobo-activati
 5699 ?        00:00:00 gnome-vfs-daemo
 5739 ?        00:00:01 gnome-screensav
 5742 ?        00:00:01 emerald
 5743 ?        00:00:10 compiz.real
 5744 ?        00:00:00 vino-session
 5749 ?        00:00:00 bluetooth-apple
 5751 ?        00:00:00 update-notifier
 5757 ?        00:00:00 evolution-alarm
 5761 ?        00:00:00 trackerd
 5763 ?        00:00:00 nm-applet
 5765 ?        00:00:00 python
 5768 ?        00:00:00 gnome-power-man
 5795 ?        00:00:00 mapping-daemon
 5799 ?        00:00:00 trashapplet
 5857 ?        00:00:00 fast-user-switc
 5859 ?        00:00:01 deskbar-applet
 5861 ?        00:00:00 mixer_applet2
 5906 ?        00:00:03 gnome-terminal
 5909 ?        00:00:00 gnome-pty-helpe
 5910 pts/0    00:00:00 bash
 5998 ?        00:00:00 notification-da
 6007 ?        00:00:00 dhclient
 6084 ?        00:00:00 firefox
 6096 ?        00:00:00 run-mozilla.sh
 6100 ?        00:00:28 firefox-bin
 6114 pts/0    00:00:00 ps


---

### Post by sdennie on 2008-04-18
It sounds like a well known problem with the 8400M GS card and the nvidia drivers.  There is a huge thread that has sort of devolved into a shouting match [here]("http://www.nvnews.net/vbulletin/showthread.php?t=101161") and I posted something [here]("http://ubuntuforums.org/showthread.php?t=747294") that is a workaround for the problem that some people have had success with.

---

### Post by ak87 on 2008-04-19
I will try to install the new Ubuntu 8 beta on laptop... Apperantly the issue should be solved there
Will be back with results...

---

### Post by ak87 on 2008-04-19
It works!

I installed the new Ubuntu 8 beta version and the nvidia drivers works great!

Thanks for all the help!

(Now onto fixing wireless....:()

---

### Post by DigifanM on 2008-04-19
> **kirsis said:**
> No, too much SWAP can't hurt. The unrequired portions are just unused, thus it's recommended not to overdo swap and put that space to use.



As for the tracker, it's an application that indexes filesw on your hard drive for fast search operations. It can slow down your system a lot, when running, but I don't see it among the top apps, so I'd guess it's not the issue. (though I'm no expert in cli task handling and such)

Good advice, I have an acer Aspire9502 and have also 2GB of RAM. if you install some screenlets so you have the ram load in sight you will see the memory is seldomly used to it's fullest. Also I run a virtual box to do video editing on XP on a USBhard drive no probs with memory.

---

### Post by n0kS on 2008-04-19
> **ak87 said:**
> Output:
direct rendering: yes

I noticed that KDE runs muck faster than GNOME... but still flashvideos lags a lot
I would prefer GNOME... hope there is fix for this problem
I have the same problem (flashvideos like youtube, metacafe and others lags a lot!!!) in my both desktop PCs
1st: 600MHz, 180MB ram, 100/200MX nVidia (no lag with winxp)
2nd. 3.2GHz dualcore, 512MB ram, 8600 GT nVidia (no lag with winxp)

I think is a general problem with the flash-nonfree package that they provide for flash videos :S

---

### Post by ak87 on 2008-04-20
It works for me, when I installed Ubuntu 8.04... I use the flash-nonfree package too, and it doesn't lag anumore :)

---

### Post by Ajay Chahar on 2008-04-20
I have exactly the same problem. I am on arch presently which runs way faster! But I also have a pekwm install of Hardy Heron which is indeed snappy.

---

### Post by fhantazm on 2008-04-20
Im running Hardy on a lowend Compaq F750US with compiz-fusion enabled and it is still faster than XP, which is saying a lot. 
Funnily enough, I am running the Eee PC XP install in VirtuaBox and thats the fastest I have EVER seen Xp run. On ANY hardware. 

Id say its definitely a driver/config problem.

---

